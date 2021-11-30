# 网格

一个网格应该至少需要一系列的顶点，每个顶点包含一个位置向量、一个法向量和一个纹理坐标向量。一个网格还应该包含用于索引绘制的索引以及纹理形式的材质数据（漫反射/镜面光贴图）。

```c
struct Vertex {
    glm::vec3 Position;
    glm::vec3 Normal;
    glm::vec2 TexCoords;
};
```

我们将所有需要的向量储存到一个叫做Vertex的结构体中，我们可以用它来索引每个顶点属性。除了Vertex结构体之外，我们还需要将纹理数据整理到一个Texture结构体中。我们储存了纹理的id以及它的类型，比如是漫反射贴图或者是镜面光贴图。

```c
struct Texture {
    unsigned int id;
    string type;
};
```

定义网格类的结构了：

```c++
class Mesh {
    public:
        /*  网格数据  */
        vector<Vertex> vertices;
        vector<unsigned int> indices;
        vector<Texture> textures;
        /*  函数  */
        Mesh(vector<Vertex> vertices, vector<unsigned int> indices, vector<Texture> textures);
        void Draw(Shader shader);
    private:
        /*  渲染数据  */
        unsigned int VAO, VBO, EBO;
        /*  函数  */
        void setupMesh();
};  
```

你可以看到这个类并不复杂。在构造器中，我们将所有必须的数据赋予了网格，我们在setupMesh函数中初始化缓冲，并最终使用Draw函数来绘制网格。注意我们将一个着色器传入了Draw函数中，将着色器传入网格类中可以让我们在绘制之前设置一些uniform（像是链接采样器到纹理单元）。

构造器的内容非常易于理解。我们只需要使用构造器的参数设置类的公有变量就可以了。我们在构造器中还调用了setupMesh函数：

```c++
Mesh(vector<Vertex> vertices, vector<unsigned int> indices, vector<Texture> textures)
{
    this->vertices = vertices;
    this->indices = indices;
    this->textures = textures;

    setupMesh();
}
```

## 初始化

由于有了构造器，我们现在有一大列的网格数据用于渲染。在此之前我们还必须配置正确的缓冲，并通过顶点属性指针定义顶点着色器的布局。现在你应该对这些概念都很熟悉了，但我们这次会稍微有一点变动，使用结构体中的顶点数据：

```c++
void setupMesh()
{
    glGenVertexArrays(1, &VAO);
    glGenBuffers(1, &VBO);
    glGenBuffers(1, &EBO);

    glBindVertexArray(VAO);
    glBindBuffer(GL_ARRAY_BUFFER, VBO);

    glBufferData(GL_ARRAY_BUFFER, vertices.size() * sizeof(Vertex), &vertices[0], GL_STATIC_DRAW);  

    glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
    glBufferData(GL_ELEMENT_ARRAY_BUFFER, indices.size() * sizeof(unsigned int), 
                 &indices[0], GL_STATIC_DRAW);

    // 顶点位置
    glEnableVertexAttribArray(0);   
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, sizeof(Vertex), (void*)0);
    // 顶点法线
    glEnableVertexAttribArray(1);   
    glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, sizeof(Vertex), (void*)offsetof(Vertex, Normal));
    // 顶点纹理坐标
    glEnableVertexAttribArray(2);   
    glVertexAttribPointer(2, 2, GL_FLOAT, GL_FALSE, sizeof(Vertex), (void*)offsetof(Vertex, TexCoords));

    glBindVertexArray(0);
}  
```

C++结构体有一个很棒的特性，它们的内存布局是连续的(Sequential)。也就是说，如果我们将结构体作为一个数据数组使用，那么它将会以顺序排列结构体的变量，这将会直接转换为我们在数组缓冲中所需要的float（实际上是字节）数组。比如说，如果我们有一个填充后的Vertex结构体，那么它的内存布局将会等于：

```c++
Vertex vertex;
vertex.Position  = glm::vec3(0.2f, 0.4f, 0.6f);
vertex.Normal    = glm::vec3(0.0f, 1.0f, 0.0f);
vertex.TexCoords = glm::vec2(1.0f, 0.0f);
// = [0.2f, 0.4f, 0.6f, 0.0f, 1.0f, 0.0f, 1.0f, 0.0f];
```

由于有了这个有用的特性，我们能够直接传入一大列的Vertex结构体的指针作为缓冲的数据，它们将会完美地转换为glBufferData所能用的参数：

```c++
glBufferData(GL_ARRAY_BUFFER, vertices.size() * sizeof(Vertex), &vertices[0], GL_STATIC_DRAW);
```

自然`sizeof`运算也可以用在结构体上来计算它的字节大小。这个应该是32字节的（8个float * 每个4字节）。

结构体的另外一个很好的用途是它的预处理指令`offsetof(s, m)`，它的第一个参数是一个结构体，第二个参数是这个结构体中变量的名字。这个宏会返回那个变量距结构体头部的字节偏移量(Byte Offset)。这正好可以用在定义glVertexAttribPointer函数中的偏移参数：

```c++
glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, sizeof(Vertex), (void*)offsetof(Vertex, Normal)); 
```

## 渲染

我们需要为Mesh类定义最后一个函数，它的Draw函数。在真正渲染这个网格之前，我们需要在调用glDrawElements函数之前先绑定相应的纹理。然而，这实际上有些困难，我们一开始并不知道这个网格（如果有的话）有多少纹理、纹理是什么类型的。所以我们该如何在着色器中设置纹理单元和采样器呢？

为了解决这个问题，我们需要设定一个命名标准：每个漫反射纹理被命名为`texture_diffuseN`，每个镜面光纹理应该被命名为`texture_specularN`，其中`N`的范围是1到纹理采样器最大允许的数字。比如说我们对某一个网格有3个漫反射纹理，2个镜面光纹理，它们的纹理采样器应该之后会被调用：

```glsl
uniform sampler2D texture_diffuse1;
uniform sampler2D texture_diffuse2;
uniform sampler2D texture_diffuse3;
uniform sampler2D texture_specular1;
uniform sampler2D texture_specular2;
```

最终的渲染代码是这样的：

```c++
void Draw(Shader shader) 
{
    unsigned int diffuseNr = 1;
    unsigned int specularNr = 1;
    for(unsigned int i = 0; i < textures.size(); i++)
    {
        glActiveTexture(GL_TEXTURE0 + i); // 在绑定之前激活相应的纹理单元
        // 获取纹理序号（diffuse_textureN 中的 N）
        string number;
        string name = textures[i].type;
        if(name == "texture_diffuse")
            number = std::to_string(diffuseNr++);
        else if(name == "texture_specular")
            number = std::to_string(specularNr++);

        shader.setFloat(("material." + name + number).c_str(), i);
        glBindTexture(GL_TEXTURE_2D, textures[i].id);
    }
    glActiveTexture(GL_TEXTURE0);

    // 绘制网格
    glBindVertexArray(VAO);
    glDrawElements(GL_TRIANGLES, indices.size(), GL_UNSIGNED_INT, 0);
    glBindVertexArray(0);
}
```


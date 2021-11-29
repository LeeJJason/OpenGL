# 基础光照

冯氏光照模型(Phong Lighting Model)的主要结构由3个分量组成：环境(Ambient)、漫反射(Diffuse)和镜面(Specular)光照

![](basic_lighting_phong.png)

- 环境光照(Ambient Lighting)：即使在黑暗的情况下，世界上通常也仍然有一些光亮（月亮、远处的光），所以物体几乎永远不会是完全黑暗的。为了模拟这个，我们会使用一个环境光照常量，它永远会给物体一些颜色。
- 漫反射光照(Diffuse Lighting)：模拟光源对物体的方向性影响(Directional Impact)。它是冯氏光照模型中视觉上最显著的分量。物体的某一部分越是正对着光源，它就会越亮。
- 镜面光照(Specular Lighting)：模拟有光泽物体上面出现的亮点。镜面光照的颜色相比于物体的颜色会更倾向于光的颜色。

# 环境光照

把环境光照添加到场景里非常简单。我们用光的颜色乘以一个很小的常量环境因子，再乘以物体的颜色，然后将最终结果作为片段的颜色：

```glsl
void main()
{
    float ambientStrength = 0.1;
    vec3 ambient = ambientStrength * lightColor;

    vec3 result = ambient * objectColor;
    FragColor = vec4(result, 1.0);
}
```

# 漫反射光照

![](diffuse_light.png)

为了测量光线和片段的角度，我们使用一个叫做**法向量(Normal Vector)**的东西，它是垂直于片段表面的一个向量（这里以黄色箭头表示），这两个向量之间的角度很容易就能够通过点乘计算出来（两个单位向量的夹角越小，它们点乘的结果越倾向于1，当两个向量的夹角为90度的时候，点乘会变为0）

点乘返回一个标量，我们可以用它计算光线对片段颜色的影响，这样不同片段朝向光源的方向的不同，这些片段被照亮的情况也不同

现在我们知道了，计算漫反射光照需要：

- 法向量：一个垂直于顶点表面的向量
- 定向的光线：作为**光源的位置**与**片段的位置**之间向量差的方向向量，为了计算这个光线，我们需要光的位置向量和片段的位置向量

## 法向量

法向量是一个垂直于顶点表面的（单位）向量，由于顶点本身并没有表面（它只是空间中一个独立的点），我们要利用它周围的顶点来计算出这个顶点的表面

```glsl
#version 330 core
layout (location = 0) in vec3 aPos;
layout (location = 1) in vec3 aNormal;

out vec3 Normal;

void main()
{
    gl_Position = projection * view * model * vec4(aPos, 1.0);
    Normal = aNormal;
}
```

## 计算漫反射光照

光源的位置向量

```glsl
uniform vec3 lightPos;
```

然后在渲染循环中（渲染循环的外面也可以，因为它不会改变）更新uniform。我们使用在前面声明的lightPos向量作为光源位置：

```c
lightingShader.setVec3("lightPos", lightPos);
```

最后，我们还需要片段的位置。我们会在世界空间中进行所有的光照计算，因此我们需要一个在世界空间中的顶点位置。我们可以通过把顶点位置属性乘以模型矩阵（不是观察和投影矩阵）来把它变换到世界空间坐标。这个在顶点着色器中很容易完成，所以我们声明一个输出变量，并计算它的世界空间坐标：

```glsl
out vec3 FragPos;  
out vec3 Normal;

void main()
{
    gl_Position = projection * view * model * vec4(aPos, 1.0);
    FragPos = vec3(model * vec4(aPos, 1.0));
    Normal = aNormal;
}
```

最后，在片段着色器中添加相应的输入变量。

```glsl
#version 330 core
out vec4 FragColor;

in vec3 Normal;  
in vec3 FragPos;  
  
uniform vec3 lightPos; 
uniform vec3 lightColor;
uniform vec3 objectColor;

void main()
{
    // ambient
    float ambientStrength = 0.1;
    vec3 ambient = ambientStrength * lightColor;
  	
    // diffuse 
    vec3 norm = normalize(Normal);
    vec3 lightDir = normalize(lightPos - FragPos);
    float diff = max(dot(norm, lightDir), 0.0);
    vec3 diffuse = diff * lightColor;
            
    //环境光分量和漫反射分量，我们把它们相加，然后把结果乘以物体的颜色，来获得片段最后的输出颜色。
    vec3 result = (ambient + diffuse) * objectColor;
    FragColor = vec4(result, 1.0);
} 
```

## 最后一件事

如果模型矩阵执行了不等比缩放，顶点的改变会导致法向量不再垂直于表面了。因此，我们不能用这样的模型矩阵来变换法向量。下面的图展示了应用了不等比缩放的模型矩阵对法向量的影响：

![](basic_lighting_normal_transformation.png)

首先，法向量只是一个方向向量，方向向量不能表达空间中的特定位置，同时，法向量没有齐次坐标（顶点位置中的w分量），也就是说**位移操作**不应该影响到法向量。对于法向量，我们只希望对它实施缩放和旋转变换。因此，如果我们打算把法向量乘以一个模型矩阵，我们就要从矩阵中移除位移部分：只选用模型矩阵左上角3×3的矩阵，或者把法向量的w分量设置为0再乘以4×4矩阵

其次，如果模型矩阵执行了**不等比缩放**，顶点的改变会导致法向量不再垂直于表面了，因此，我们不能用这样的模型矩阵来变换法向量。修复的方法是使用一个为法向量专门定制的模型矩阵，这个矩阵称之为**法线矩阵(Normal Matrix)**，它使用了一些线性代数的操作来移除对法向量错误缩放的影响。

法线矩阵被定义为「**模型矩阵左上角 的逆矩阵 的转置矩阵**」，如果你不明白这是什么意思，别担心，我们还没有讨论逆矩阵(Inverse Matrix)和转置矩阵(Transpose Matrix)，注意，大部分的资源都会将法线矩阵定义为应用到模型-观察矩阵(Model-view Matrix)上的操作，但是由于我们只在世界空间中进行操作（不是在观察空间），我们只使用模型矩阵

现在，在顶点着色器中，我们可以使用inverse和transpose函数自己生成这个法线矩阵，这两个函数对所有类型矩阵都有效。注意我们还要把被处理过的矩阵强制转换为3×3矩阵，来保证它失去了位移属性以及能够乘以`vec3`的法向量

```glsl
Normal = mat3(transpose(inverse(model))) * aNormal;
```

即使是对于着色器来说，逆矩阵也是一个开销比较大的运算，因此，只要可能就应该避免在着色器中进行逆矩阵运算，它们必须为你场景中的每个顶点都进行这样的处理，当然我们用作学习目这样做是可以的，但是对于一个对效率有要求的应用来说，在绘制之前你最好用CPU计算出法线矩阵，然后通过uniform把值传递给着色器（像模型矩阵一样）

# 镜面光照

和漫反射光照一样，镜面光照也是依据光的方向向量和物体的法向量来决定的，但是它也依赖于观察方向，例如玩家是从什么方向看着这个片段的。镜面光照是基于光的反射特性。如果我们想象物体表面像一面镜子一样，那么，无论我们从哪里去看那个表面所反射的光，镜面光照都会达到最大化。你可以从下面的图片看到效果：

![](basic_lighting_specular_theory.png)

为了得到观察者的世界空间坐标，我们简单地使用摄像机对象的位置坐标代替（它当然就是观察者）。所以我们把另一个uniform添加到片段着色器，把相应的摄像机位置坐标传给片段着色器：

```c
uniform vec3 viewPos;

lightingShader.setVec3("viewPos", camera.Position);
```

现在我们已经获得所有需要的变量，可以计算高光强度了。首先，我们定义一个镜面强度(Specular Intensity)变量，给镜面高光一个中等亮度颜色，让它不要产生过度的影响。

```
float specularStrength = 0.5;
```

计算视线方向向量，和对应的沿着法线轴的反射向量：

```c
vec3 viewDir = normalize(viewPos - FragPos);
vec3 reflectDir = reflect(-lightDir, norm);
```

需要注意的是我们对`lightDir`向量进行了取反。`reflect`函数要求第一个向量是**从**光源指向片段位置的向量，但是`lightDir`当前正好相反，是从片段**指向**光源（由先前我们计算`lightDir`向量时，减法的顺序决定）。为了保证我们得到正确的`reflect`向量，我们通过对`lightDir`向量取反来获得相反的方向。第二个参数要求是一个法向量，所以我们提供的是已标准化的`norm`向量。

剩下要做的是计算镜面分量。下面的代码完成了这件事：

```glsl
float spec = pow(max(dot(viewDir, reflectDir), 0.0), 32);
vec3 specular = specularStrength * spec * lightColor
```

我们先计算视线方向与反射方向的点乘（并确保它不是负值），然后取它的32次幂。这个32是高光的反光度(Shininess)。一个物体的反光度越高，反射光的能力越强，散射得越少，高光点就会越小。在下面的图片里，你会看到不同反光度的视觉效果影响：

![](basic_lighting_specular_shininess.png)

在光照着色器的早期，开发者曾经在顶点着色器中实现冯氏光照模型。在顶点着色器中做光照的优势是，相比片段来说，顶点要少得多，因此会更高效，所以（开销大的）光照计算频率会更低。然而，顶点着色器中的最终颜色值是仅仅只是那个顶点的颜色值，片段的颜色值是由插值光照颜色所得来的。结果就是这种光照看起来不会非常真实，除非使用了大量顶点。

![](basic_lighting_gouruad.png)
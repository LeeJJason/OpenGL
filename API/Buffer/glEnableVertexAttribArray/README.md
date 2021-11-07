## C Specification

```

void glEnableVertexAttribArray(GLuint index);
 
void glDisableVertexAttribArray(GLuint index);
 
void glEnableVertexArrayAttrib(GLuint vaobj, GLuint index);
 
void glDisableVertexArrayAttrib(GLuint vaobj, GLuint index);
```

## Parameters

- **`vaobj`**

  指定顶点数组对象的名称，用于`glDisableVertexArrayAttrib`和`glEnableVertexArrayAttrib`函数。

- **`index`**

  指定启用或禁用的通用顶点属性的索引。

## Description

`glEnableVertexAttribArray` and `glEnableVertexArrayAttrib` enable the generic vertex attribute array specified by *`index`*. `glEnableVertexAttribArray` uses currently bound vertex array object for the operation, whereas `glEnableVertexArrayAttrib` updates state of the vertex array object with ID *`vaobj`*.

`glDisableVertexAttribArray` and `glDisableVertexArrayAttrib` disable the generic vertex attribute array specified by *`index`*. `glDisableVertexAttribArray` uses currently bound vertex array object for the operation, whereas `glDisableVertexArrayAttrib` updates state of the vertex array object with ID *`vaobj`*.

By default, all client-side capabilities are disabled, including all generic vertex attribute arrays. If enabled, the values in the generic vertex attribute array will be accessed and used for rendering when calls are made to vertex array commands such as [glDrawArrays](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glDrawArrays.xhtml), [glDrawElements](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glDrawElements.xhtml), [glDrawRangeElements](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glDrawRangeElements.xhtml), [glMultiDrawElements](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glMultiDrawElements.xhtml), or [glMultiDrawArrays](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glMultiDrawArrays.xhtml).



```
当我们特别谈论到顶点着色器的时候，每个输入变量也叫顶点属性(Vertex Attribute)。我们能声明的顶点属性是有上限的，它一般由硬件来决定。OpenGL确保至少有16个包含4分量的顶点属性可用，但是有些硬件或许允许更多的顶点属性，你可以查询GL_MAX_VERTEX_ATTRIBS来获取具体的上限：

默认情况下，出于性能考虑，所有顶点着色器的属性（Attribute）变量都是关闭的，意味着数据在着色器端是不可见的，哪怕数据已经上传到GPU，由glEnableVertexAttribArray启用指定属性，才可在顶点着色器中访问逐顶点的属性数据。glVertexAttribPointer或VBO只是建立CPU和GPU之间的逻辑连接，从而实现了CPU数据上传至GPU。但是，数据在GPU端是否可见，即，着色器能否读取到数据，由是否启用了对应的属性决定，这就是glEnableVertexAttribArray的功能，允许顶点着色器读取GPU（服务器端）数据。
```



## 参考资料

[OPENGL学习笔记之glEnableVertexAttribArray函数](https://blog.csdn.net/gongxun1994/article/details/78271870)

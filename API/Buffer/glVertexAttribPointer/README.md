## vC Specification

```c
void glVertexAttribPointer(GLuint index, GLint size, GLenum type, GLboolean normalized, GLsizei stride, const void * pointer);
 
void glVertexAttribIPointer(GLuint index, GLint size, GLenum type, GLsizei stride, const void * pointer);
 
void glVertexAttribLPointer(GLuint index, GLint size, GLenum type, GLsizei stride, const void * pointer);
```

## Parameters

**`index`**

Specifies the index of the generic vertex attribute to be modified.

指定被改变的通用顶点属性得索引

**`size`**

指定每个通用顶点属性的组件数量。必须是1, 2, 3, 4。此外，常量符号`GL_BGRA`被`glVertexAttribPointer`接受，值为 4.

**`type`**

指定阵列中每个组件的数据类型。常量符合`GL_BYTE`, `GL_UNSIGNED_BYTE`, `GL_SHORT`, `GL_UNSIGNED_SHORT`, `GL_INT`, 和`GL_UNSIGNED_INT`被`glVertexAttribPointer`和`glVertexAttribIPointer`所接受。此外，`GL_HALF_FLOAT`, `GL_FLOAT`, `GL_DOUBLE`, `GL_FIXED`, `GL_INT_2_10_10_10_REV`, `GL_UNSIGNED_INT_2_10_10_10_REV` 和`GL_UNSIGNED_INT_10F_11F_11F_REV`被`glVertexAttribPointer`接受。`GL_DOUBLE`也被`glVertexAttribLPointer`接受，并且是该函数的*`type`*参数接受的唯一标志。初始值为`GL_FLOAT`。

**`normalized`**

对于`glVertexAttribPointer`，具体说明在访问 fixed-point 数据值时，是应将其规范化（`GL_TRUE`）还是直接转换为 fixed-point值（`GL_FALSE`）。

**`stride`**

指定连续通用顶点属性之间的字体偏移。如果*`stride`* 是 0，则一般顶点属性被理解为紧密地包装在阵列中。初始值为 0。

**`pointer`**

指定缓冲区数据存储中当前与`GL_ARRAY_BUFFER` 目标绑定的缓冲器中第一个通用顶点属性的第一个组件的偏移。初始值为 0。


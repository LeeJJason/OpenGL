## C Specification

```c
void glBindVertexArray(	GLuint array);
```

## Parameters

- **`array`**

  指定用于绑定的顶点数组对象的名称

  

## Description

`glBindVertexArray`将顶点数组对象与*`array`*名称绑定。*`array`* 是调用[glGenVertexArrays](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glGenVertexArrays.xhtml)返回得顶点数组对象的名称或用 0 来断开现有的顶点数组对象的绑定。

如果没有名称为*`array`*的顶点数组对象，*`array`* 若为首次绑定，则创建。如果绑定成功，则不会更改顶点数组对象的状态，并且任何以前的顶点数组对象绑定被破坏。
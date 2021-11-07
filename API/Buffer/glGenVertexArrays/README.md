## C Specification

```c
void glGenVertexArrays(GLsizei n, GLuint *arrays);
```

生成顶点数组对象

## Parameters

- **`n`**

  指定生成顶点数组对象名称得数量

- **`arrays`**

  指定存放生成顶点数组对象名称的数组

## Description

`glGenVertexArrays` 返回 *`n`* 个顶点数组对象名称存放在 *`arrays`*. 不能保证名称构成一组连续的整数; 但是，能保证返回的名称在调用**glGenVertexArrays**之前没有被使用

通过调用`glGenVertexArrays` 返回的顶点数组对象名称不会通过后续呼叫返回，除非它们首先被[glDeleteVertexArrays](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glDeleteVertexArrays.xhtml) 删除。

在*`arrays`*中返回得名称被标记为已使用， `glGenVertexArrays`仅有目的，但它们仅在首次绑定时获得状态和类型。


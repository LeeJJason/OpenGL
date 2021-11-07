## C Specification

```c
void glDeleteBuffers(GLsizei n,	const GLuint * buffers);
```

删除命名的缓冲对象

## Parameters

**`n`**

指定需要删除的缓冲对象的数量

**`buffers`**

指定一个被删除得缓冲对象的数组

## Description

**glDeleteBuffers**删除由数组缓冲区的元素命名的*n*个缓冲区对象。 删除缓冲区对象后，它就没有内容了，其名称可以被重用（例如[glGenBuffers](https://blog.csdn.net/flycatdeng/article/details/82667132)调用生成该名称（ID））。如果删除当前绑定的缓冲区对象，则绑定将恢复为0（缺少任何缓冲区对象）。

## Errors

**GL_INVALID_VALUE**：*n*是负数

## 参考资料

* [glDeleteBuffers](https://www.khronos.org/registry/OpenGL-Refpages/gl4/)


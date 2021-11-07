## C Specification

```c
void glGenBuffers(GLsizei n, GLuint * buffers);
```

生成缓冲对象的名称

## Parameters

**`n`**

指定要生成缓冲对象名称得数量

**`buffers`**

指定一个数组用于存放生成缓冲对象的名称



`glGenBuffers()函数仅仅是生成一个缓冲对象的名称，这个缓冲对象并不具备任何意义，它仅仅是个缓冲对象，还不是一个顶点数组缓冲，它类似于C语言中的一个指针变量，我们可以分配内存对象并且用它的名称来引用这个内存对象。OpenGL有很多缓冲对象类型，那么这个缓冲对象到底是什么类型，就要用到 glBindBuffer 函数了。`

## Description

**glGenBuffers** 返回 n 个当前未使用的缓存对象名称，并保存到 buffers 数组中。返回到 buffers 中的名称不一定是连续的整型数据。但是，保证在调用**glGenBuffers**之前没有在使用中。

通过调用 **glGenBuffers** 返回的缓存对象的名称，不会在后续调用中返回，除非首先通过 [glDeleteBuffers](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glDeleteBuffers.xhtml) 删除。

没有缓存对象与返回的缓存对象名称关联，除非首先调用 [glBindBuffer](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glBindBuffer.xhtml) 绑定。

## Errors

**GL_INVALID_VALUE**：*n*是负数

## 参考资料

* [glGenBuffers](https://www.khronos.org/registry/OpenGL-Refpages/gl4/)
* [glGenBuffers与glBindBuffer理解](https://blog.csdn.net/qq_36383623/article/details/85123077)


## C Specification

```c
void glGenFramebuffers(	GLsizei n, GLuint *ids);
```

## Parameters

**n**

```
指定生成的 framebuffer 对象名称得数量
```


**ids**

```
指定一个用于存放生成的 framebuffer 对象名称的数组
```


## Description

glGenFramebuffers 在 ids 中返回 n 个帧缓冲器对象名称。不能保证这些名称形成一组连续的整数;但是，可以保证在调用 glGenFramebuffers 之前，没有一个返回的名称在立即使用。

通过调用 glGenFramebuffers 返回的帧缓冲器对象名称不会被后续调用返回，除非首先使用 glDeleteFramebuffers 删除它们。

id 中返回的名称被标记为已使用，仅用于 glGenFramebuffers 的目的，但它们仅在首次绑定时才获取状态和类型。

## C Specification

```c
void glBindFramebuffer(	GLenum target, GLuint framebuffer);
```

## Parameters

***target ***Specifies the framebuffer target of the binding operation.

```
指定绑定操作的 framebuffer 目标
```


***framebuffer ***

```
指定用于绑定的 framebuffer 对象的名称
```



## Description

glBindFramebuffer 将名称为 framebuffer 的帧缓冲区对象绑定到 target 目指定的帧缓冲区目标。目标必须是GL_DRAW_FRAMEBUFFER、GL_READ_FRAMEBUFFER或GL_FRAMEBUFFER。如果帧缓冲器对象绑定到GL_DRAW_FRAMEBUFFER或GL_READ_FRAMEBUFFER，则它分别成为呈现或回读操作的目标，直到它被删除或另一个帧缓冲器绑定到相应的绑定点。调用目标设置为GL_FRAMEBUFFER的 glBindFramebuffer 会将帧缓冲器绑定到读取和绘制帧缓冲器目标。*`framebuffer`*是先前从对 glGenFramebuffers 的调用返回的帧缓冲器对象的名称，或 0 用于断开帧缓冲器对象与*  target 目的现有绑定。

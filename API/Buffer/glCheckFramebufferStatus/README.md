## C Specification

```c
GLenum glCheckFramebufferStatus(GLenum target);
GLenum glCheckNamedFramebufferStatus(GLuint framebuffer,  GLenum target);
```


## Parameters

`target`

指定为 glCheckFramebufferStatus 绑定帧缓冲器的目标，以及为 `glCheckNamedFramebufferStatus` 检查帧缓冲器完整性的目标。

*`framebuffer`*

指定 `glCheckNamedFramebufferStatus` 的帧缓冲器对象的名称

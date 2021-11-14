## C Specification

```c
void glClear(	GLbitfield mask);
```

## Parameters

**`mask`**

Bitwise OR of masks that indicate the buffers to be cleared. The three masks are `GL_COLOR_BUFFER_BIT`, `GL_DEPTH_BUFFER_BIT`, and `GL_STENCIL_BUFFER_BIT`.

指示要清除缓冲的位 OR 掩码。三个掩码：`GL_COLOR_BUFFER_BIT`, `GL_DEPTH_BUFFER_BIT`, 和`GL_STENCIL_BUFFER_BIT`。

*`GL_COLOR_BUFFER_BIT`*

指示当前启用的颜色缓冲区。

*`GL_DEPTH_BUFFER_BIT`*

指示深度缓冲区

*`GL_STENCIL_BUFFER_BIT`*

指示模版缓冲区
## C Specification

```c
void glGenerateMipmap(	GLenum target);
void glGenerateTextureMipmap(	GLuint texture);
```

## Parameters

**`target`**

指定为`glGenerateTextureMipmap`绑定的纹理目标对象。必须是 `GL_TEXTURE_1D`, `GL_TEXTURE_2D`, `GL_TEXTURE_3D`, `GL_TEXTURE_1D_ARRAY`, `GL_TEXTURE_2D_ARRAY`, `GL_TEXTURE_CUBE_MAP`, or `GL_TEXTURE_CUBE_MAP_ARRAY`之一。

**`texture`**

指定用于`glGenerateTextureMipmap`的纹理对象名称。


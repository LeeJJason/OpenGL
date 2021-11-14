## C Specification

```c
void glBindTexture(	GLenum target, GLuint texture);
```

## Parameters

**`target`**

指定绑定哪种纹理.。必须是其中一种 `GL_TEXTURE_1D`, `GL_TEXTURE_2D`, `GL_TEXTURE_3D`, `GL_TEXTURE_1D_ARRAY`, `GL_TEXTURE_2D_ARRAY`, `GL_TEXTURE_RECTANGLE`, `GL_TEXTURE_CUBE_MAP`, `GL_TEXTURE_CUBE_MAP_ARRAY`, `GL_TEXTURE_BUFFER`, `GL_TEXTURE_2D_MULTISAMPLE` 或 `GL_TEXTURE_2D_MULTISAMPLE_ARRAY`.

**`texture`**

指定纹理的名称。


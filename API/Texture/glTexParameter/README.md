## C Specification

```c
void glTexParameterf(	GLenum target,
 	GLenum pname,
 	GLfloat param);
 
void glTexParameteri(	GLenum target,
 	GLenum pname,
 	GLint param);
 
void glTextureParameterf(	GLuint texture,
 	GLenum pname,
 	GLfloat param);
 
void glTextureParameteri(	GLuint texture,
 	GLenum pname,
 	GLint param);
 
void glTexParameterfv(	GLenum target,
 	GLenum pname,
 	const GLfloat * params);
 
void glTexParameteriv(	GLenum target,
 	GLenum pname,
 	const GLint * params);
 
void glTexParameterIiv(	GLenum target,
 	GLenum pname,
 	const GLint * params);
 
void glTexParameterIuiv(	GLenum target,
 	GLenum pname,
 	const GLuint * params);
 
void glTextureParameterfv(	GLuint texture,
 	GLenum pname,
 	const GLfloat *params);
 
void glTextureParameteriv(	GLuint texture,
 	GLenum pname,
 	const GLint *params);
 
void glTextureParameterIiv(	GLuint texture,
 	GLenum pname,
 	const GLint *params);
 
void glTextureParameterIuiv(	GLuint texture,
 	GLenum pname,
 	const GLuint *params);
```

## Parameters

**`target`**

指定`glTexParameter`函数绑定的 texture 对象。必须是其中之一：`GL_TEXTURE_1D`, `GL_TEXTURE_1D_ARRAY`, `GL_TEXTURE_2D`, `GL_TEXTURE_2D_ARRAY`, `GL_TEXTURE_2D_MULTISAMPLE`, `GL_TEXTURE_2D_MULTISAMPLE_ARRAY`, `GL_TEXTURE_3D`, `GL_TEXTURE_CUBE_MAP`, `GL_TEXTURE_CUBE_MAP_ARRAY`, 或者 `GL_TEXTURE_RECTANGLE`。

**`texture`**

指定用于 `glTextureParameter` 函数的 texture 对象名称

**`pname`**

指定单值纹理参数的符号名称。*`pname`* 是一下之一：`GL_DEPTH_STENCIL_TEXTURE_MODE`, `GL_TEXTURE_BASE_LEVEL`, `GL_TEXTURE_COMPARE_FUNC`, `GL_TEXTURE_COMPARE_MODE`, `GL_TEXTURE_LOD_BIAS`, `GL_TEXTURE_MIN_FILTER`, `GL_TEXTURE_MAG_FILTER`, `GL_TEXTURE_MIN_LOD`, `GL_TEXTURE_MAX_LOD`, `GL_TEXTURE_MAX_LEVEL`, `GL_TEXTURE_SWIZZLE_R`, `GL_TEXTURE_SWIZZLE_G`, `GL_TEXTURE_SWIZZLE_B`, `GL_TEXTURE_SWIZZLE_A`, `GL_TEXTURE_WRAP_S`, `GL_TEXTURE_WRAP_T`, 或者 `GL_TEXTURE_WRAP_R`。

对于向量命令 (`glTexParameter*v`), *`pname`* 可以是其中之一 `GL_TEXTURE_BORDER_COLOR` 或者 `GL_TEXTURE_SWIZZLE_RGBA`.

**`param`**

用于标量命令，指定  *`pname`* 的值

**`params`**

对于矢量命令，指定指向存储  *`pname`*值或值的数组的指针。


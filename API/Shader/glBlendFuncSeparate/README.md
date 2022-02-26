## C Specification

```C

void glBlendFuncSeparate(	GLenum srcRGB,
 	GLenum dstRGB,
 	GLenum srcAlpha,
 	GLenum dstAlpha);
 
void glBlendFuncSeparatei(	GLuint buf,
 	GLenum srcRGB,
 	GLenum dstRGB,
 	GLenum srcAlpha,
 	GLenum dstAlpha);
```

## Parameters

**`buf`**

For `glBlendFuncSeparatei`, specifies the index of the draw buffer for which to set the blend functions.

**`srcRGB`**

Specifies how the red, green, and blue blending factors are computed. The initial value is `GL_ONE`.

**`dstRGB`**

Specifies how the red, green, and blue destination blending factors are computed. The initial value is `GL_ZERO`.

**`srcAlpha`**

Specified how the alpha source blending factor is computed. The initial value is `GL_ONE`.

**`dstAlpha`**

Specified how the alpha destination blending factor is computed. The initial value is `GL_ZERO`.
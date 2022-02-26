## C Specification

```C

void glBlendFunc(	GLenum sfactor,
 	GLenum dfactor);
 
void glBlendFunci(	GLuint buf,
 	GLenum sfactor,
 	GLenum dfactor);
```

## Parameters	

**`buf`**

For `glBlendFunci`, specifies the index of the draw buffer for which to set the blend function.

**`sfactor`**

Specifies how the red, green, blue, and alpha source blending factors are computed. The initial value is `GL_ONE`.

**`dfactor`**

Specifies how the red, green, blue, and alpha destination blending factors are computed. The following symbolic constants are accepted: `GL_ZERO`, `GL_ONE`, `GL_SRC_COLOR`, `GL_ONE_MINUS_SRC_COLOR`, `GL_DST_COLOR`, `GL_ONE_MINUS_DST_COLOR`, `GL_SRC_ALPHA`, `GL_ONE_MINUS_SRC_ALPHA`, `GL_DST_ALPHA`, `GL_ONE_MINUS_DST_ALPHA`. `GL_CONSTANT_COLOR`, `GL_ONE_MINUS_CONSTANT_COLOR`, `GL_CONSTANT_ALPHA`, and `GL_ONE_MINUS_CONSTANT_ALPHA`. The initial value is `GL_ZERO`.
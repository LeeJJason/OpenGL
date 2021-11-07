## C Specification

```c
GLuint glCreateShader(	GLenum shaderType);
```

创建shader对象

## Parameters

**`shaderType`**

指定创建的shader类型。必须是其中一种 `GL_COMPUTE_SHADER`, `GL_VERTEX_SHADER`, `GL_TESS_CONTROL_SHADER`, `GL_TESS_EVALUATION_SHADER`, `GL_GEOMETRY_SHADER`, 或者 `GL_FRAGMENT_SHADER`.
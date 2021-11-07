## C Specification

```c
void glGetShaderiv(GLuint shader, GLenum pname, GLint *params);
```

## Parameters

- **`shader`**

  指定shader对象

- **`pname`**

  指定对象参数.接受得符号为 `GL_SHADER_TYPE`, `GL_DELETE_STATUS`, `GL_COMPILE_STATUS`, `GL_INFO_LOG_LENGTH`, `GL_SHADER_SOURCE_LENGTH`.

- **`params`**

  返回请求的对象参数

## Description

`glGetShader` 返回指定shader对象的 *`params`* 值。已定义的值如下:

- *`GL_SHADER_TYPE`*

  *`params`* returns `GL_VERTEX_SHADER` if *`shader`* is a vertex shader object, `GL_GEOMETRY_SHADER` if *`shader`* is a geometry shader object, and `GL_FRAGMENT_SHADER` if *`shader`* is a fragment shader object.

- *`GL_DELETE_STATUS`*

  *`params`* returns `GL_TRUE` if *`shader`* is currently flagged for deletion, and `GL_FALSE` otherwise.

- *`GL_COMPILE_STATUS`*

  *`params`* returns `GL_TRUE` if the last compile operation on *`shader`* was successful, and `GL_FALSE` otherwise.

- *`GL_INFO_LOG_LENGTH`*

  *`params`* returns the number of characters in the information log for *`shader`* including the null termination character (i.e., the size of the character buffer required to store the information log). If *`shader`* has no information log, a value of 0 is returned.

- *`GL_SHADER_SOURCE_LENGTH`*

  *`params`* returns the length of the concatenation of the source strings that make up the shader source for the *`shader`*, including the null termination character. (i.e., the size of the character buffer required to store the shader source). If no source code exists, 0 is returned.
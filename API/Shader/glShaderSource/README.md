## C Specification

```c
void glShaderSource(GLuint shader, GLsizei count, const GLchar **string, const GLint *length);
```

更新shader对象的源码

## Parameters

**`shader`**

Specifies the handle of the shader object whose source code is to be replaced.

指定shader对象的句柄用于更新源码

**`count`**

Specifies the number of elements in the *`string`* and *`length`* arrays.

指定*`string`* 和*`length`* 数组的数量

**`string`**

Specifies an array of pointers to strings containing the source code to be loaded into the shader.

指定一个包含源码字符串指针数组，用于加载到shader中

**`length`**

指定字符创数组长度
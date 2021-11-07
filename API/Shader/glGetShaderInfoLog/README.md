## C Specification

```c
void glGetShaderInfoLog(GLuint shader, GLsizei maxLength, GLsizei *length, GLchar *infoLog);
```

返回指定的shader对象的log信息。

## Parameters

**`shader`**

指定获取log信息的shader对象

**`maxLength`**

Specifies the size of the character buffer for storing the returned information log.

指定存放返回log的字符缓冲大小

**`length`**

Returns the length of the string returned in *`infoLog`* (excluding the null terminator).

返回*`infoLog`*的字符串长度（不包含null 结束符）

**`infoLog`**

Specifies an array of characters that is used to return the information log.

指定一个字符数组，用于返回log信息


## C Specification

```c
void glGetBooleanv(	GLenum pname,
 	GLboolean * data);
 
void glGetDoublev(	GLenum pname,
 	GLdouble * data);
 
void glGetFloatv(	GLenum pname,
 	GLfloat * data);
 
void glGetIntegerv(	GLenum pname,
 	GLint * data);
 
void glGetInteger64v(	GLenum pname,
 	GLint64 * data);
 
void glGetBooleani_v(	GLenum target,
 	GLuint index,
 	GLboolean * data);
 
void glGetIntegeri_v(	GLenum target,
 	GLuint index,
 	GLint * data);
 
void glGetFloati_v(	GLenum target,
 	GLuint index,
 	GLfloat * data);
 
void glGetDoublei_v(	GLenum target,
 	GLuint index,
 	GLdouble * data);
 
void glGetInteger64i_v(	GLenum target,
 	GLuint index,
 	GLint64 * data);
```

## Parameters

- **`pname`**

  指定非索引版本的`glGet`要返回的参数值。接受下面列表中符号常数。

- **`target`**

  指定要返回的`glGet`索引版本的参数值。接受下面列表中符号常数。

- **`index`**

  指定被查询的特定元素的索引。

- **`data`**

  返回指定参数的值或值。
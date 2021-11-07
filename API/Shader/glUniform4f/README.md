## C Specification

```c

void glUniform1f(	GLint location,
 	GLfloat v0);
 
void glUniform2f(	GLint location,
 	GLfloat v0,
 	GLfloat v1);
 
void glUniform3f(	GLint location,
 	GLfloat v0,
 	GLfloat v1,
 	GLfloat v2);
 
void glUniform4f(	GLint location,
 	GLfloat v0,
 	GLfloat v1,
 	GLfloat v2,
 	GLfloat v3);
 
void glUniform1i(	GLint location,
 	GLint v0);
 
void glUniform2i(	GLint location,
 	GLint v0,
 	GLint v1);
 
void glUniform3i(	GLint location,
 	GLint v0,
 	GLint v1,
 	GLint v2);
 
void glUniform4i(	GLint location,
 	GLint v0,
 	GLint v1,
 	GLint v2,
 	GLint v3);
 
void glUniform1ui(	GLint location,
 	GLuint v0);
 
void glUniform2ui(	GLint location,
 	GLuint v0,
 	GLuint v1);
 
void glUniform3ui(	GLint location,
 	GLuint v0,
 	GLuint v1,
 	GLuint v2);
 
void glUniform4ui(	GLint location,
 	GLuint v0,
 	GLuint v1,
 	GLuint v2,
 	GLuint v3);
 
void glUniform1fv(	GLint location,
 	GLsizei count,
 	const GLfloat *value);
 
void glUniform2fv(	GLint location,
 	GLsizei count,
 	const GLfloat *value);
 
void glUniform3fv(	GLint location,
 	GLsizei count,
 	const GLfloat *value);
 
void glUniform4fv(	GLint location,
 	GLsizei count,
 	const GLfloat *value);
 
void glUniform1iv(	GLint location,
 	GLsizei count,
 	const GLint *value);
 
void glUniform2iv(	GLint location,
 	GLsizei count,
 	const GLint *value);
 
void glUniform3iv(	GLint location,
 	GLsizei count,
 	const GLint *value);
 
void glUniform4iv(	GLint location,
 	GLsizei count,
 	const GLint *value);
 
void glUniform1uiv(	GLint location,
 	GLsizei count,
 	const GLuint *value);
 
void glUniform2uiv(	GLint location,
 	GLsizei count,
 	const GLuint *value);
 
void glUniform3uiv(	GLint location,
 	GLsizei count,
 	const GLuint *value);
 
void glUniform4uiv(	GLint location,
 	GLsizei count,
 	const GLuint *value);
 
void glUniformMatrix2fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
 
void glUniformMatrix3fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
 
void glUniformMatrix4fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
 
void glUniformMatrix2x3fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
 
void glUniformMatrix3x2fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
 
void glUniformMatrix2x4fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
 
void glUniformMatrix4x2fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
 
void glUniformMatrix3x4fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
 
void glUniformMatrix4x3fv(	GLint location,
 	GLsizei count,
 	GLboolean transpose,
 	const GLfloat *value);
```

## Parameters

- **`location`**

  指定需要修改的 uniform 变量得位置

- **`count`**

  对于向量（`glUniform*v`）命令，指定要修改的元素数量。如果目标均匀变量不是数组，则此应为 1，如果是数组，则应为 1 或更多。对于矩阵（`glUniformMatrix*`）命令，指定要修改的矩阵数量。如果目标均匀变量不是矩阵数组，则此应为 1，如果是矩阵数组，则此应为 1 或更多。

- **`transpose`**

  For the matrix commands, specifies whether to transpose the matrix as the values are loaded into the uniform variable.

  对于矩阵命令，指定是否在值加载到 uniform 变量时转置矩阵。

- **`v0`\*, \*`v1`\*, \*`v2`\*, \*`v3`**

  对于标量命令，指定用于指定 uniform 变量的新值。

- **`value`**

  For the vector and matrix commands, specifies a pointer to an array of *`count`* values that will be used to update the specified uniform variable.

  对于矢量和矩阵命令，指定指向将用于更新指定 uniform 变量的数组的 *`count`*。


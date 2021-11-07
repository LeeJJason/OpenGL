## C Specification

```glsl
void glDrawArrays(GLenum mode, GLint first, GLsizei count);
```

## Parameters

- **`mode`**

  指定渲染的图元。常量符号为： `GL_POINTS`, `GL_LINE_STRIP`, `GL_LINE_LOOP`, `GL_LINES`, `GL_LINE_STRIP_ADJACENCY`, `GL_LINES_ADJACENCY`, `GL_TRIANGLE_STRIP`, `GL_TRIANGLE_FAN`, `GL_TRIANGLES`, `GL_TRIANGLE_STRIP_ADJACENCY`, `GL_TRIANGLES_ADJACENCY` 和 `GL_PATCHES`

- **`first`**

  指定启用的数组的开始所有

- **`count`**

  指定用于渲染的索引数量
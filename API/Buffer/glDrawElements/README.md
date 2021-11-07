## C Specification

```c
void glDrawElements(GLenum mode, GLsizei count, GLenum type, const void * indices);
```

从数组中渲染图元

## Parameters

- **`mode`**

  指定渲染的图元。常量符号： `GL_POINTS`, `GL_LINE_STRIP`, `GL_LINE_LOOP`, `GL_LINES`, `GL_LINE_STRIP_ADJACENCY`, `GL_LINES_ADJACENCY`, `GL_TRIANGLE_STRIP`, `GL_TRIANGLE_FAN`, `GL_TRIANGLES`, `GL_TRIANGLE_STRIP_ADJACENCY`, `GL_TRIANGLES_ADJACENCY` 和`GL_PATCHES` 

- **`count`**

  指定渲染的元素数量

- **`type`**

  Specifies the type of the values in *`indices`*. Must be one of `GL_UNSIGNED_BYTE`, `GL_UNSIGNED_SHORT`, or `GL_UNSIGNED_INT`.

  指定 *`indices`* 中的值类型。必须是`GL_UNSIGNED_BYTE`, `GL_UNSIGNED_SHORT`, 或者`GL_UNSIGNED_INT` 中一个

- **`indices`**

  指定存放索引的指针

  

## Description

**glDrawElements** 用很少的子程序调用指定多个几何图元。 无需调用 **GL** 函数来传递每个单独的顶点、法线、纹理坐标、边缘标志或颜色，您可以预先指定单独的顶点、法线等数组，并使用它们通过一次调用构建一系列图元 到 **glDrawElements**。

当 **glDrawElements** 被调用时，它使用来自已启用数组的计数顺序元素，从索引开始构造几何图元序列。 mode 指定构造什么样的基元以及数组元素如何构造这些基元。 如果启用了多个阵列，则使用每个阵列。

由 **glDrawElements** 修改的顶点属性在 **glDrawElements** 返回后具有未指定的值。 未修改的属性保持其先前的值。


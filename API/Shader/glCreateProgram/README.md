## C Specification

```c
GLuint glCreateProgram(	void);
```

## Description

**glCreateProgram** 创建一个空程序对象，并返回一个可以引用它的非零值。程序对象是可以连接到着色器对象的对象。这提供了一个机制来指定将链接到创建程序的着色器对象。它还提供了一种检查用于创建程序的检测兼容性的手段（例如，检查顶点阴影和碎片阴影之间的兼容性）。当不再需要作为程序对象的一部分时，可以分离着色器对象。这些可执行程序在调用 glUseProgram 时成为当前状态的一部分。程序对象可以通过调用 [glDeleteProgram](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glDeleteProgram.xhtml)来删除。当程序对象不再是当前上下文渲染状态的一部分时，将删除与程序对象相关的记忆。

通过[glAttachShader](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glAttachShader.xhtml) 成功将着色器对象与 连接到程序对象中，成功用  [glCompileShader](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glCompileShader.xhtml) 编译shader对象，并成功用[glLinkProgram](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glLinkProgram.xhtml) 将程序对象与连接起来，从而在程序对象中创建一个或多个可执行对象。这些可执行程序在调用[glUseProgram](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glUseProgram.xhtml) 时成为当前状态的一部分。程序对象可以通过调用[glDeleteProgram](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glDeleteProgram.xhtml)来删除。当程序对象不再是当前上下文渲染状态的一部分时，将删除与程序对象相关的记忆。


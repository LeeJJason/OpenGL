## C Specification

```c
void glBufferData(GLenum target, GLsizeiptr size, const void * data, GLenum usage);
void glNamedBufferData(GLuint buffer, GLsizeiptr size, const void *data, GLenum usage);
```

创建和初始化一个缓存对象的存储数据

## Parameters

- **`target`**

  指定用于`glBufferData`绑定缓存对象的目标，必须是下面表中的一种缓存绑定目标:

  | **Buffer Binding Target**      | **Purpose**                        |
  | ------------------------------ | ---------------------------------- |
  | `GL_ARRAY_BUFFER`              | Vertex attributes                  |
  | `GL_ATOMIC_COUNTER_BUFFER`     | Atomic counter storage             |
  | `GL_COPY_READ_BUFFER`          | Buffer copy source                 |
  | `GL_COPY_WRITE_BUFFER`         | Buffer copy destination            |
  | `GL_DISPATCH_INDIRECT_BUFFER`  | Indirect compute dispatch commands |
  | `GL_DRAW_INDIRECT_BUFFER`      | Indirect command arguments         |
  | `GL_ELEMENT_ARRAY_BUFFER`      | Vertex array indices               |
  | `GL_PIXEL_PACK_BUFFER`         | Pixel read target                  |
  | `GL_PIXEL_UNPACK_BUFFER`       | Texture data source                |
  | `GL_QUERY_BUFFER`              | Query result buffer                |
  | `GL_SHADER_STORAGE_BUFFER`     | Read-write storage for shaders     |
  | `GL_TEXTURE_BUFFER`            | Texture data buffer                |
  | `GL_TRANSFORM_FEEDBACK_BUFFER` | Transform feedback buffer          |
  | `GL_UNIFORM_BUFFER`            | Uniform block storage              |

- **`buffer`**

  指定用于 `glNamedBufferData` 函数得缓存对象的名称

- **`size`**

  指定缓存对象的新数据存储的字节大小

- **`data`**

  指定指向数据的指针，这些数据将被复制到数据存储中进行初始化，如果没有数据要复制，则指定为"NULL"。

- **`usage`**

  指定数据存储的预期使用模式。 常量符合必须为 `GL_STREAM_DRAW`, `GL_STREAM_READ`, `GL_STREAM_COPY`, `GL_STATIC_DRAW`, `GL_STATIC_READ`, `GL_STATIC_COPY`, `GL_DYNAMIC_DRAW`, `GL_DYNAMIC_READ`, or `GL_DYNAMIC_COPY`.

## Description

*`usage`* 能被拆分为两部分: 第一部分, 访问频率（修改和使用），其次，访问的性质。

访问频率可能是其中之一：

- *STREAM*

  数据存储内容将修改一次，最多使用几次。

- *STATIC*

  数据存储内容将修改一次并多次使用。

- *DYNAMIC*

  数据存储内容将反复修改并多次使用。

访问性质可能是其中之一

- *DRAW*

  数据存储内容由应用程序修改，并用作 GL 绘图和图像规范命令的源。

- *READ*

  数据存储内容通过阅读来自 GL 的数据进行修改，并在应用程序查询时用于返回该数据。

- *COPY*

  数据存储内容通过从 GL 读取数据进行修改，并用作 GL 绘图和图像规范命令的源。
## C Specification

```c
void glBindBuffer(GLenum target, GLuint buffer);
```

绑定一个命名的缓存对象

## Parameters

## Parameters

- **`target`**

  指定缓存对象绑定类型，必须是下面表中的一种缓存绑定目标:

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

  指定缓存对象的名称。


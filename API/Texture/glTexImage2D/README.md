## C Specification

```c
void glTexImage2D(	GLenum target,
 	GLint level,
 	GLint internalformat,
 	GLsizei width,
 	GLsizei height,
 	GLint border,
 	GLenum format,
 	GLenum type,
 	const void * data);
```

## Parameters

**`target`**

指定目标纹理. 必须是 `GL_TEXTURE_2D`, `GL_PROXY_TEXTURE_2D`, `GL_TEXTURE_1D_ARRAY`, `GL_PROXY_TEXTURE_1D_ARRAY`, `GL_TEXTURE_RECTANGLE`, `GL_PROXY_TEXTURE_RECTANGLE`, `GL_TEXTURE_CUBE_MAP_POSITIVE_X`, `GL_TEXTURE_CUBE_MAP_NEGATIVE_X`, `GL_TEXTURE_CUBE_MAP_POSITIVE_Y`, `GL_TEXTURE_CUBE_MAP_NEGATIVE_Y`, `GL_TEXTURE_CUBE_MAP_POSITIVE_Z`, `GL_TEXTURE_CUBE_MAP_NEGATIVE_Z`, or `GL_PROXY_TEXTURE_CUBE_MAP`.

**`level`**

指定 level-of-detail 数字。 级别 0 是基础图像级别. 级别 *n* 是 *n*th mipmap 缩小图像。 如果 *`target`* 是 `GL_TEXTURE_RECTANGLE` 或者`GL_PROXY_TEXTURE_RECTANGLE`, *`level`* 必须 0.

**`internalformat`**

指定纹理中的颜色组件数量。必须是表 1 中给出的基本内部格式之一，表 2 中给出的大小内部格式之一，或表 3 中给出的压缩内部格式之一。

**`width`**

指定纹理图像的宽度。所有实现都支持至少 1024 texels 宽的纹理图像。

**`height`**

Specifies the height of the texture image, or the number of layers in a texture array, in the case of the `GL_TEXTURE_1D_ARRAY` and `GL_PROXY_TEXTURE_1D_ARRAY` targets. All implementations support 2D texture images that are at least 1024 texels high, and texture arrays that are at least 256 layers deep.

在`GL_TEXTURE_1D_ARRAY`和`GL_PROXY_TEXTURE_1D_ARRAY`目标的情况下，指定纹理图像的高度或纹理数组中的层数。所有实现都支持至少 1024 texels 高的 2D 纹理图像，以及至少 256 层深的纹理阵列。

**`border`**

必须为0

**`format`**

指定像素数据的格式。接受以下符号值: `GL_RED`, `GL_RG`, `GL_RGB`, `GL_BGR`, `GL_RGBA`, `GL_BGRA`, `GL_RED_INTEGER`, `GL_RG_INTEGER`, `GL_RGB_INTEGER`, `GL_BGR_INTEGER`, `GL_RGBA_INTEGER`, `GL_BGRA_INTEGER`, `GL_STENCIL_INDEX`, `GL_DEPTH_COMPONENT`, `GL_DEPTH_STENCIL`.

**`type`**

指定像素数据的数据类型。接受以下符号值: `GL_UNSIGNED_BYTE`, `GL_BYTE`, `GL_UNSIGNED_SHORT`, `GL_SHORT`, `GL_UNSIGNED_INT`, `GL_INT`, `GL_HALF_FLOAT`, `GL_FLOAT`, `GL_UNSIGNED_BYTE_3_3_2`, `GL_UNSIGNED_BYTE_2_3_3_REV`, `GL_UNSIGNED_SHORT_5_6_5`, `GL_UNSIGNED_SHORT_5_6_5_REV`, `GL_UNSIGNED_SHORT_4_4_4_4`, `GL_UNSIGNED_SHORT_4_4_4_4_REV`, `GL_UNSIGNED_SHORT_5_5_5_1`, `GL_UNSIGNED_SHORT_1_5_5_5_REV`, `GL_UNSIGNED_INT_8_8_8_8`, `GL_UNSIGNED_INT_8_8_8_8_REV`, `GL_UNSIGNED_INT_10_10_10_2`, and `GL_UNSIGNED_INT_2_10_10_10_REV`.

**`data`**

指定内存中图像数据的指点。



Table 1. Base Internal Formats

| **Base Internal Format** | **RGBA, Depth and Stencil Values** | **Internal Components** |
| :----------------------- | :--------------------------------- | :---------------------- |
| `GL_DEPTH_COMPONENT`     | Depth                              | D                       |
| `GL_DEPTH_STENCIL`       | Depth, Stencil                     | D, S                    |
| `GL_RED`                 | Red                                | R                       |
| `GL_RG`                  | Red, Green                         | R, G                    |
| `GL_RGB`                 | Red, Green, Blue                   | R, G, B                 |
| `GL_RGBA`                | Red, Green, Blue, Alpha            | R, G, B, A              |
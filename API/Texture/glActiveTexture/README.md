## C Specification

```c
void glActiveTexture(	GLenum texture);
```

## Parameters

**`texture`**

指定要使活动状态的纹理单元。纹理单位的数量取决于实现，但必须至少为 80 个。*`texture`*必须是`GL_TEXTURE`*i*中一个，i必须是0到`GL_MAX_COMBINED_TEXTURE_IMAGE_UNITS` - 1 的值之间。初始值是 `GL_TEXTURE0`。




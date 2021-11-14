## Declaration

```c
gvec4 texture(	gsampler1D sampler,
 	float P,
 	[float bias]);
 
gvec4 texture(	gsampler2D sampler,
 	vec2 P,
 	[float bias]);
 
gvec4 texture(	gsampler3D sampler,
 	vec3 P,
 	[float bias]);
 
gvec4 texture(	gsamplerCube sampler,
 	vec3 P,
 	[float bias]);
 
float texture(	sampler1DShadow sampler,
 	vec3 P,
 	[float bias]);
 
float texture(	sampler2DShadow sampler,
 	vec3 P,
 	[float bias]);
 
float texture(	samplerCubeShadow sampler,
 	vec4 P,
 	[float bias]);
 
gvec4 texture(	gsampler1DArray sampler,
 	vec2 P,
 	[float bias]);
 
gvec4 texture(	gsampler2DArray sampler,
 	vec3 P,
 	[float bias]);
 
gvec4 texture(	gsamplerCubeArray sampler,
 	vec4 P,
 	[float bias]);
 
float texture(	sampler1DArrayShadow sampler,
 	vec3 P,
 	[float bias]);
 
float texture(	gsampler2DArrayShadow sampler,
 	vec4 P,
 	[float bias]);
 
gvec4 texture(	gsampler2DRect sampler,
 	vec2 P);
 
float texture(	sampler2DRectShadow sampler,
 	vec3 P);
 
float texture(	gsamplerCubeArrayShadow sampler,
 	vec4 P,
 	float compare);
```

## Parameters

- **`sampler`**

  指定取样器，将从其中检索到的纹理被绑定。

- **`P`**

  指定纹理采样的纹理坐标。

- **`bias`**

  指定在详细计算过程中应用的可选偏差。

- **`compare`**

  指定从"格桑普勒立方体"阴影取样时，将比较取取的特克斯的值。
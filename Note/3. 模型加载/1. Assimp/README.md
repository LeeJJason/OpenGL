# Assimp

这些所谓的3D建模工具(3D Modeling Tool)可以让艺术家创建复杂的形状，并使用一种叫做UV映射(uv-mapping)的手段来应用贴图。这些工具将会在导出到模型文件的时候自动生成所有的顶点坐标、顶点法线以及纹理坐标。这样子艺术家们即使不了解图形技术细节的情况下，也能拥有一套强大的工具来构建高品质的模型了。所有的技术细节都隐藏在了导出的模型文件中。但是，作为图形开发者，我们就**必须**要了解这些技术细节了。

## 模型加载库

一个非常流行的模型导入库是[Assimp](http://assimp.org/)，它是**Open Asset Import Library**（开放的资产导入库）的缩写。Assimp能够导入很多种不同的模型文件格式（并也能够导出部分的格式），它会将所有的模型数据加载至Assimp的通用数据结构中。当Assimp加载完模型之后，我们就能够从Assimp的数据结构中提取我们所需的所有数据了。由于Assimp的数据结构保持不变，不论导入的是什么种类的文件格式，它都能够将我们从这些不同的文件格式中抽象出来，用同一种方式访问我们需要的数据。

当使用Assimp导入一个模型的时候，它通常会将整个模型加载进一个**场景**(Scene)对象，它会包含导入的模型/场景中的所有数据。Assimp会将场景载入为一系列的节点(Node)，每个节点包含了场景对象中所储存数据的索引，每个节点都可以有任意数量的子节点。Assimp数据结构的（简化）模型如下：

![](assimp_structure.png)

- 和材质和网格(Mesh)一样，所有的场景/模型数据都包含在Scene对象中。Scene对象也包含了场景根节点的引用。
- 场景的Root node（根节点）可能包含子节点（和其它的节点一样），它会有一系列指向场景对象中mMeshes数组中储存的网格数据的索引。Scene下的mMeshes数组储存了真正的Mesh对象，节点中的mMeshes数组保存的只是场景中网格数组的索引。
- 一个Mesh对象本身包含了渲染所需要的所有相关数据，像是顶点位置、法向量、纹理坐标、面(Face)和物体的材质。
- 一个网格包含了多个面。Face代表的是物体的渲染图元(Primitive)（三角形、方形、点）。一个面包含了组成图元的顶点的索引。由于顶点和索引是分开的，使用一个索引缓冲来渲染是非常简单的（见[你好，三角形](https://learnopengl-cn.github.io/01 Getting started/04 Hello Triangle/)）。
- 最后，一个网格也包含了一个Material对象，它包含了一些函数能让我们获取物体的材质属性，比如说颜色和纹理贴图（比如漫反射和镜面光贴图）。

## 构建Assimp

你可以在Assimp的[下载页面](http://assimp.org/main_downloads.html)中选择相应的版本。在写作时使用的Assimp最高版本为3.1.1。我们建议你自己编译Assimp库，因为它们的预编译库在大部分系统上都是不能运行的。如果你忘记如何使用CMake自己编译一个库的话，可以复习[创建窗口](https://learnopengl-cn.github.io/01 Getting started/02 Creating a window/)小节。

构建Assimp时可能会出现一些问题，所以我会将它们的解决方案列在这里，便于大家排除错误：

- CMake在读取配置列表时，不断报出DirectX库丢失的错误。报错如下：

```
Could not locate DirectX
CMake Error at cmake-modules/FindPkgMacros.cmake:110 (message):
Required library DirectX not found! Install the library (including dev packages) 
and try again. If the library is already installed, set the missing variables 
manually in cmake.
```


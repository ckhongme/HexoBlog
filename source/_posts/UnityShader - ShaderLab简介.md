---
title: UnityShader - ShaderLab简介
date: 2019-04-01
tags: [UnityShader]
categories: Unity
---

在学习UnityShader之前，先了解一下Shader是什么；
# Shader
### 什么是Shader？
Shader（着色器）是一段规定好输入（颜色，贴图等）和输出（渲染器能够读懂的点和颜色的对应关系）的代码；
### Shader有什么用？
- 对于可编程管线，设置顶点可以改变形状，设置像素可以改变颜色；
- 可以做很多CPU下编程做不到(很难)的事情。例如半透明、UV动画、遮挡剔除、色彩斑斓的blend混合，Fog等；

### Shader的特点？
C#编码是在CPU角度；而Shader编码是在GPU角度；
#### 其他需要知道的知识点
这里只是简要提一下，详细请自行查阅相关内容；

#### 1.发送渲染命令的流程：*应用程序 ->接口 -> 显卡驱动 -> GPU*
- 应用程序：
- 图像应用编程接口：DirectX和OpenGL；
- 显卡驱动：负责与图像编程接口和GPU打交道，例如NVIDIA；
- GPU：最后成像；

（应用程序通过图形接口将数据存储在显存（Video Random Access Memory，VRAM）中，再通过图形接口发送DrawCall渲染命令，DrawCall被显卡驱动翻译成CPU理解的代码后进行真正的绘制）

#### 2.用于编写着色器代码的语言：*Shading Language*
- 在Windows下图形渲染是**DirectX**，DirectX使用 HLSL（High Level Shading Language）编写shader；
- 在Linux下图形渲染是**OpenGL**，OpenGL使用GLSL（OpenGL Shading Language）编写shader；
- NVIDIA和微软合作提供的**Cg**（C for Graphic），语法跟HLSL非常相像，可以无缝移植成HLSL代码，DirectX和OpenGL都支持；

（应用程序通过图形接口将数据存储在显存（Video Random Access Memory，VRAM）中，再通过图形接口发送DrawCall渲染命令，DrawCall被显卡驱动翻译成CPU理解的代码后进行真正的绘制）

#### 3.从数据到最终成像的过程：*渲染管线*
- **固定管线**：老显卡是不能编程的，功能是固定的；
- **可编程管线**：新显卡可以对顶点和像素进行编程处理；



# UnityShader

### 什么是UnityShader？
UnityShader实际上指的就是一个ShaderLab文件（后缀为.shader的文件），是用ShaderLab语言编写的，重点支持Cg语言；

**关于ShaderLab**
- 是 Unity 提供的，用于编写 Unity Shader 的一种说明性语言;
- 定义了Unity要显示一个材质所需要的所有东西，不仅仅是着色器代码；
- 可以理解成经Unity封装的Shader文件；

### UnityShader有什么用？
**处理渲染问题：**
- 实现一些特殊效果；
- 与美术对接，指导美术绘制相关贴图；
- 性能优化；

### Unity相关知识
MeshFilter用于存储一个Mesh；MeshRenderer用于渲染一个模型的外观；
GameObject里有MeshRenderer，MeshRenderer里有Material列表，材质球Material是Shader的容器，每个Material里有且只有一个Shader；

Unity可以直接创建的UnitySahder类型：
- Standard Surface Shader - 产生一个包含标准光照模型的表面着色器模板。
- Unlit Shader（推荐） - 产生一个不包含光照（但包含雾效）的基本顶点/片元着色器。
- Image Effect Shader - 为实现各种屏幕处理后效果提供的基本模板。
- Compute Shader - 特殊Shader，利用GPU的并行特性计算一些计算
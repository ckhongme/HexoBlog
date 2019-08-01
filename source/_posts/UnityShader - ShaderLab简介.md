---
title: UnityShader - ShaderLab简介
date: 2019-03-01
tags: [UnityShader, ShaderLab, Shader]
categories: Unity
---

在我们学习UnityShader的时候，

### 什么是Shader？

Shader（着色器）是一段规定好输入（颜色，贴图等）和输出（渲染器能够读懂的点和颜色的对应关系）的代码；
给定了输入，然后给输出进行着色


### 什么是UnityShader？

UnityShader实际上指的就是一个ShaderLab文件（后缀为.shader的文件），是用ShaderLab语言编写的，重点支持Cg语言；

**关于ShaderLab**
- 是 Unity 提供的，用于编写 Unity Shader 的一种说明性语言;
- 定义了Unity要显示一个材质所需要的所有东西，不仅仅是着色器代码；
- 文件的后缀是.shader；

### UnityShader有什么用？

**处理渲染问题：**
- 实现一些特殊效果；
- 与美术对接，指导美术绘制相关贴图；
- 性能优化；

### UnityShader的特点

分类：
Standard Surface Shader - 产生一个包含标准光照模型的表面着色器模板。
	2. 
Unlit Shader（推荐） - 产生一个不包含光照（但包含雾效）的基本顶点/片元着色器。
	3. 
Image Effect Shader - 为实现各种屏幕处理后效果提供的基本模板。
	4. 
Compute Shader - 特殊Shader，利用GPU的并行特性计算一些计算


MeshFilter用于存储一个Mesh；MeshRenderer用于渲染一个模型的外观；
GameObject里有MeshRenderer，MeshRenderer里有Material列表，材质球Material是Shader的容器，每个Material里有且只有一个Shader；


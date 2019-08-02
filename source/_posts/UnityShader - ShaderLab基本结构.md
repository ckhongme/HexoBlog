---
title: UnityShader - ShaderLab基本结构
date: 2019-04-04
tags: [UnityShader, FragmentShader, SurfaceShader]
categories: Unity
---


## 整体结构
按照我的分法，UnityShader主要分成两大类，一类是表面着色器（Surface Shader)，一类是定点着色器和片元着色器（Vertex Shader & Fragment Shader）
```
Shader "位置/Name"
{
    Properties { // 第一部分 }
    SubShader { // 第二部分 }
    Fallback "Diffuse" // 第三部分
}
```

### Properties属性（第一部分）
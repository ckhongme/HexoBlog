---
title: UnityShader - ShaderLab整体结构
date: 2019-04-05
tags: [UnityShader]
categories: Unity
---

# 整体结构
按照我的分法，UnityShader主要分成两大类，一类是表面着色器（Surface Shader)，一类是定点着色器和片元着色器（Vertex Shader & Fragment Shader）；
后面我会再具体讲讲这两类UnityShader的区别；

现在先来看看UnityShader的整体结构：
```
Shader "Path/Name"
{
    Properties { // 第一部分 }
    SubShader { // 第二部分 }
    Fallback "Diffuse" // 第三部分
}
```
*Shader关键字后面跟一个字符串对该着色器进行命名，可以通过添加Path加以分类；*

## Properties 属性（第一部分）
**1.属性的作用**：充当数据接口，将外部的数据资源引入，以供着色器内部使用；
**2.属性的使用**：
- **外部设置**：通过声明属性，可以方便在Hierarchy面板对Shader的参数进行设置；
- **内部访问**：通过在Cg代码片中定义和这些属性类型相匹配，名字相同的变量，可以在Shader内部中访问；*（cg代码块后面会解释）*

**3.属性的格式**：
在Properties语义块中声明属性，需要指定默认值，声明后会出现在材质面板中；
`_属性名称 （“显示名称”，属性类型）= 默认值`

例如声明一个2D类型的贴图变量：
```
Properties
{
    _MainTex("Main Texture", 2D) = "black" {}
}
```

**4.常见的属性类型**：

| Texture贴图相关  |变量相关|
| ------------ | ------------ |
| 2D(纹理贴图)|Color(颜色)|
|3D(纹理贴图)|Vector(表示4个元素的向量，xyzw)|
|Cube(三维纹理)| int  | 
||  float |
||  Range(表示范围值) |

*更多具体的书写格式，请查看我的另外一篇文章：*[UnityShader常用术语查询](https://ckhongme.github.io/2019/04-10/UnityShader%20-%20UnityShader%E5%B8%B8%E7%94%A8%E6%9C%AF%E8%AF%AD%E6%9F%A5%E8%AF%A2/)

## SubShader 子着色器 （第二部分）
SubShader可以有多个，但至少要有一个；
加载时，Unity会选择第一个能够在目标平台上运行的SubShader；

SubShader的基本结构：
```
SubShader
{
    标签设置 [可选]
    LOD设置 [可选]
    渲染状态设置 [可选]
    cg代码块
}
```

### 标签设置 [可选]

**标签的作用**：
是UnityShader和渲染引擎之间的沟通桥梁，硬件通过判断Tags来决定何时应该调用该子着色器；
**标签的格式**：
键值对（键和值都是字符串类型）
`Tags { "键1" = "值1"  "键2" = "值2"}`
例如：规定在绘制透明或者半透明图形时调用，指定渲染队列为透明队列，且不受投影的影响；
`Tags { "RenderType" = "Transparent" "Queue" = "Transparent"  "IgnoreProjector" = "True"  }`

### LOD设置 [可选]
**LOD的作用**：Level of Detail的缩写，当系统设定的最大LOD小于SubShader制定的LOD时，该SubShader不可用；

### 渲染状态设置 [可选]
**渲染状态的作用**：决定了一个潜在像素是否被扔掉，或写入帧内；
**设置状态的格式**：
`状态名 状态值`
**常见的状态设置**

| Cull Off  | ZWrite Off  | ZTest Off  | Blend On |
| :------------ | :------------ | :------------ | :------------ |
| 关闭背面裁剪  | 关闭深度写入 | 关闭深度测试  | 开启混合模式 |
| 半透需要看到背面 | 不遮挡其他东西时需要关 | / | / |

如果在SubShader进行设置的话，将会应用于所有的Pass，可以在Pass中再次定义覆盖；

### CG代码块
着色器代码要写在 **CGPROGRAM** 和 **ENDCG** 之间；
- 表面着色器不需要定义Pass，所以cg代码直接写在SubShader中；
- 顶点/片元着色器需要定义Pass，所以cg代码写在SubShader定义的Pass语义块中；

**CG代码块的格式**：

SurfaceShader的写法
```
CGPROGRAM

编译指令（表明写的是SufrfaceShader）
对应的CG变量
Input结构体
表面着色函数

ENDCG
```
Vertex/Fragment Shader的写法
```
SubShader
{
	Pass
	{
		Name "Pass名称"
		Tags{}
		CGPROGRAM
		...(着色器代码)
		ENDCG
	}
}
```
*具体的着色器代码，将会在后面对表面着色器以及顶点/片元着色单独的文章中进行学习，这里只是简单提一下两者的区别；*


## 第三部分   Fallback 回滚
**Fallback的作用**：设置最低级别的Pass；
相当于替代方案，当没有找到合适的SubShader时会调用；
`Fallback "name" 或者 Fallback Off`














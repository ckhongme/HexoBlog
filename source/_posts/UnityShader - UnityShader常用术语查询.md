---
title: UnityShader - 常用术语查询
date: 2019-04-10
tags: [UnityShader, ShaderLab, Shader]
categories: Unity
---

关于UnityShader常用到的术语，会随着学习的进度持续在这篇文章中更新；

---

# 变量

## 变量类型（UnityShader的属性）

| 变量  | 类型  | 写法  |
| :------------ | :------------ | :------------ |
| Int   |  整数类型 | \_Int ( "Int", Int) = 2  |
| Float   | 浮点数类型  | \_Float ( "FloatValue"，Float ) = 0.0  |
|  Range(min,max) |  范围值类型  | \_Range ( "Range"，Range( 0.5, 1.0 )) = 1.0  |
| Color  | 颜色类型  | \_Color ( "MainColor"，Color ) = (1,1,1,1)  |
| Vector  | 向量类型    | \_Vector ( "Vector4", Vector ) = (1,1,1,1)  |
|  2D  | 2D纹理贴图  | \_MainTex ( "Base(RGB)"，2D ) = "white" { }   |
| 3D     | 3D纹理贴图  | \_3D("3D", 3D) = "black" { }  |
| Cube   | 三维纹理  | \_CubeTex ( "3DMap"，Cube ) = "white" { }  |

## 变量类型（CG程序）

| 变量  | 类型  |
| :------------ | :------------ |
| int    | 32位整形数据  |
| half  | 16位浮点数据  |
| float  | 32位浮点数据，一个符号位  |
| fixed   | 12位定点数  |
| sampler\*  | 纹理对象的句柄，分为sampler、sampler1D、sampler2D、sampler3D、samplerCUBE和samplerRECT  |
| bool  | 布尔数据，被所有的图形接口支持 |
| string  | 字符类型  |

## ShaderLab与CG的变量类型匹配
| ShaderLab  | CG  |
| :------------ | :------------ |
| Color/Vector  |  float4/half4/fixed4 |
| Range/Float   | float/half/fixed  |
| 2D  | sample2D  |
| Cube  | sampleCube  |
| 3D  | sample3D  |

## UnityShader内置的时间变量

| 名称  | 类型  | 说明  |
| :------------ | :------------ | :------------ |
| _Time   |  float4  | t是自该场景加载开始所经过的时间,4个分量分别是(t/20, t, 2t, 3t) |
| _SinTime|  float4  | t是时间的正弦值,4个分量的值分别是(t/8, t/4, t/2, t) |
| _CosTime    |  float4  |t是时间的余弦值,4个分量的值分别是(t/8, t/4, t/2, t)|
| unity_DeltaTime   |  float4  | dt是时间增量,4个分量分别是(dt, 1/dt, smoothDt, 1/smoothDt) |

---
 
# 标签

## 标签类型（用于SubShader）
| 标签  | 作用  |
| :------------ | :------------ |
| Queue  | 定义渲染顺序  |
| RenderType   | Unity可以运行时替换符合特定RenderType的所有Shader  |
| DisableBatching   | 是否使用批处理  |
| ForceNoShadowCasting  | 值为"true"时，表示不接受投射阴影  |
| IgnoreProjector   | 值为"true"时，表示不接受Projector组件的投影；通常用于半透明物体；  |
| CanUseSpriteAtlas  | 当用于sprite时，将该标签设为False  |
| PreviewType  | 材质预览类型，默认是球形；可以设置成Plane，Skybox等；  |

#### RenderType 渲染类型
| 渲染类型  |  用途 |
| :------------ | :------------ |
|Opaque   | 绝大部分不透明的物体都使用这个  |
|  Transparent  | 绝大部分透明的物体、包括粒子特效都使用这个  |
| Background   | 天空盒都使用这个  |
| Overlay   | GUI、镜头光晕都使用这个  |

#### Queue 渲染队列参数
| 渲染队列  | 数值  | 应用场景  |
| :------------ | :------------ | :------------ |
| Background  | 1000  | 最早被调用的渲染，用来渲染天空盒或者背景  |
| Geometry   | 2000  | 默认值，用来渲染非透明物体（场景中的绝大多数物体应该是非透明的） |
| AlphaTest  | 2450  | 用来渲染经过AlphaTest的像素，单独为AlphaTest设定一个Queue是出于对效率的考虑  |
| Transparent  |  3000 | 以从后往前的顺序渲染透明物体  |
| Overlay  | 4000  |  用来渲染叠加的效果，是渲染的最后阶段（比如镜头光晕等特效） |

## 标签类型（用于Pass）
| 标签  |  作用 |
| :------------ | :------------ |
| LightMode  | 定义该Pass在渲染流水线中的角色  |
| RequireOptions  | 指定需要满足的条件  |

---

# LOD 数值
在Unity的Quality Settings中我们可以设定允许的最大LOD，当设定的LOD小于SubShader所指定的LOD时，这个SubShader将不可用；

| LOD  | 数值  |
| :------------ | :------------ |
| VertexLit及其系列 | 100  |
| Decal, Reflective VertexLit   | 150  |
| Diffuse | 200  |
| Diffuse Detail, Reflective Bumped Unlit, Reflective Bumped VertexLit   | 250  |
| Bumped, Specular     | 300  |
| Bumped Specular       |  400 |
| Parallax | 500  |
| Parallax Specular   | 600 |

---

# 渲染状态
| 状态参数 | 作用  |
| :------------ | :------------ |
| Cull  | 设置剔除模式：剔除背面Back/正面Front/关闭Off  |
| ZTest  | 深度测试  |
| ZWrite  | 深度写入：开启On/关闭Off |
|  Blend |  混合模式 |

---

# 语义

## 应用程序 -> 顶点函数 （a2v）
| 语义名称  | 意义  |
| :------------ | :------------ |
| POSITION | 顶点坐标（模型空间下的）  |
| NORMAL  | 法线( 模型空间下，用于计算光照)  |
|  TANGENT |  切线（模型空间下） |
|  TEXCOORD0~ｎ | 纹理坐标  |
| COLOR  |  顶点颜色 |

## 顶点函数 -> 片元函数（v2f）
| 语义名称  | 意义  |
| :------------ | :------------ |
| SV_POSITION | 剪裁空间中的顶点坐标（一般是系统直接使用）  |
| COLOR0  | 可以传递一组值 4个  |
|  COLOR1 | 可以传递一组值 4个 |
|  TEXCOORD0~7  | 传递纹理坐标，但不是必需的  |

---
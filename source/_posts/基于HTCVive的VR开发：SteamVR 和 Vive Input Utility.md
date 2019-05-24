---
title: 基于HTCVive的VR开发：SteamVR 和 Vive Input Utility
date: 2019-05-24
tags: [HTCVive, SteamVR]
categories: VR开发
---

早期用Vive开发VR，主要是基于手柄（也就是HTC Vive Controller），随着头显的版本更新，现在已经有了跟踪器（HTC Vive Tracker）以及最新的Valve Knuckles控制器；

下面主要介绍使用 **Vive Controller** 开发的基本入门，主要是 **如何通过代码获取控制器的状态和输入**；

### 原生SteamVR插件
如果要搭建一套自己的交互系统时，需用到SteamVR自身的底层代码；
(基于SteamVR Plugin 1.0+ 版本)

 - 引用命名空间：`using Valve.VR;`
 - 获取手柄对象： `var trackedObj = GetComponent<SteamVR_TrackedObject>();`
 - 判断手柄状态：
 ```
 int index = (int)trackedObject.index;
 index == -1) return;  	//当index为-1时，表示手柄没有开启
 ```
	- 获取手柄Transform：
 	`Transform controllerObj = trackedObj.transform;`
    - 获取手柄设备的输入：
    `var device = SteamVR_Controller.Input((int)trackedObj.index));`

	- 获取按键的状态： (下面以按键Trigger为例)
	```
	//按下按键（扣下扳机）
	bool isDown = device.GetPressDown(SteamVR_Controller.ButtonMask.Trigger);
	//松开按键（松开扳机）
	bool isUp = device.GetPressUp(SteamVR_Controller.ButtonMask.Trigger);
	//长按按键（长扣扳机）
	bool isPress = device.GetPress(SteamVR_Controller.ButtonMask.Trigger);
	```

    - 获取按键Pad的触摸坐标：`Vector2 vector = device.GetAxis();`

 - 调用手柄震动：`device.TriggerHapticPulse();`

### Vive Input Utility插件
如果只需要常用的功能，可以使用 Vive Input Utility 插件，该插件可以使VR开发变得更加简单；
** 该插件左右手柄是区分开的，下面以右手柄HandRole.RightHand为例 **
(基于Vive Input Utility1.47版本)

 - 引用命名空间：`using HTC.UnityPlugin.Vive;`
 - 判断手柄状态：
 ```
 var index = ViveRole.GetDeviceIndex(HandRole.RightHand);
 if(!ViveRole.IsValidIndex(index)) return;		
 ```
 - 监听手柄按键：
	```
	bool isDown = ViveInput.GetPressDown(HandRole.RightHand, ControllerButton.Trigger);
	bool isUp = ViveInput.GetPressUp(HandRole.RightHand, ControllerButton.Trigger);
	bool isPress = ViveInput.GetPress(HandRole.RightHand, ControllerButton.Trigger);
	```
 - 获取按键Pad的触摸坐标：
 `Vector2 vector = ViveInput.GetPadTouchAxis(HandRole.RightHand);`
 - 获取扳机Trigger的按下程度：
 `float value = ViveInput.GetTriggerValue(HandRole.RightHand);`
 - 手柄震动：`ViveInput.TriggerHapticPulse(HandRole.RightHand);`
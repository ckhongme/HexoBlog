---
title: 使用SteamVR sdk2.0+版本时，如何在Unity中适配Tracker
date: 2019-11-06
tags: [HTCVive, SteamVR]
categories: VR开发
---

自从SteamVR plugin for Unity（后面简称steamVR sdk）升级到2.0+版本之后，就引入了 SteamVR Input 输入系统，目的是将具体的输入设备与游戏逻辑分开，让开发者可以专心根据功能来开发，而不需要关注设备的具体按键；

但这个升级也改变了很多steamVR sdk原本的脚本，使得部分之前用 steamVR sdk 1.0+版本开发的同学一下子适应不过来，下面我主要讲讲使用 steamVR sdk2.0+版本时，要如何在Unity中适配 Tracker；


## A.在Unity端的操作
1. 通过Unity的AssetStore获取最新版本的SteamVR sdk；

**注意**：如果导入新版的SDK之后，报了下面这个错：
``[SteamVR] Error during OpenVR Init: Init_InterfaceNotFound``
说明请求的接口不存在，steamVr runtime目前的版本不兼容sdk的接口，需要更新 runtime，这在下面对SteamVR Runtime的设置中回进行；

2. 在Unity菜单栏下选中Window->SteamVR Input，在弹出的窗口选择 Yes;
<div align=center>
	<img width=500 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110811.png">
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110814.png"
</div> 
3. 在SteamVR Input窗口，保持默认就好，然后选择 Save and generate；
<div align=center>
	<img width=500 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110812.png">
</div>
5. 此时会发现Project面板多了下面三个文件夹；
<div align=center>
	<img width=300 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110813.png">
</div>
6. 将 [CameraRig] 下的两个 Controller 上的 Pose Action 设置成 \actions\default\in\Pose, 然后把 InputSource 分别设置成 LeftHand 和 RightHand；
<div align=center>
	<img width=500 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110802.png">
</div>


## B.对SteamVR Runtime的设置
1. 打开Steam并登陆账号（不登陆的话后面有些操作进行不了），然后更新SteamVR runtime的版本；
2. 通过Steam上的VR打开SteamVR runtime；
<div align=center>
	<img width=300 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110801.png">
</div>
3. 通过 Steam VR runtime 进入“控制器输入按键设置”窗口；
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110803.png">
</div>
4. 选择Unity中正在开发的应用程序；
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110804.png">
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110805.png">
</div>
5. 将当前控制器设置成 Vive Tracker in Hand；
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110806.png">
</div>
6. 点击管理定位器，将对应的 Tracker 设置成**手持**，并分别设置成**左右手**；
<div align=center>
	<img width=500 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110807.png">
</div>
7. 如果当前按键设置为空，点击创建新按键设置；
<div align=center>
	<img width=300 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110808.png">
</div>
8. 在default中勾选镜像模式，然后选择**编辑动作姿势**；
<div align=center>
	<img width=600 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110809.png">
</div>
9. 将 左手Origin 设置成**Pose**；
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/SteamVR2.0_19110810.png">
</div>
10. 最后保存个人按键设置；

**注意**: 如果点了保存之后，一直显示在上传或者没有反应，可以尝试重启下SteamVR Runtime；



按步骤设置完之后，应该就可以在Unity中运行steamVR sdk的Demo时看到我们的Tracker了，匹配Tracker的基本操作我就不再详述了，enjoy your game；
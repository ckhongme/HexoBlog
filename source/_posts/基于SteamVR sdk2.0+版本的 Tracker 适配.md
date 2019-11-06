---
title: 使用SteamVR sdk2.0+版本时，如何在Unity中适配Tracker
date: 2019-11-06
tags: [HTCVive, SteamVR]
categories: VR开发
---

自从SteamVR plugin for Unity（后面简称steamVR sdk）升级到2.0+版本之后，就引入了 SteamVR Input 输入系统，目的是将具体的输入设备与游戏逻辑分开，让开发者可以专心根据功能来开发，而不需要关注设备的具体按键或者触摸盘；

但是这个升级，也改变了很多steamVR sdk原本的脚本，使得部分之前用 steamVR sdk 1.0+版本开发的同学一下子适应不过来，很多同学在场景中都找不到Controller和Tracker了，下面我主要讲讲使用 steamVR sdk2.0+版本时，要如何在Unity中适配 Tracker；


## A.安装SDK和更新SteamVR runtime
1. 通过 UnityHub 给 Unity 安装Android开发需要的SDK；（Quest属于安卓设备）
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052801.png">
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052802.png">
</div>
2. 到AssetStore下载最新版的[Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022)，导入到Unity ；（我下的是1.73版本） 
需要注意的是1.73版本的Oculus SDK支持的Unity版本最低是 2018.2;
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052803.png">
</div>
导入后，会提示你更新到最新的OVRPlugin（1.37.0)，然后重启Unity；
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052804.png">
</div>


## B.对Oculus SDK的设置
**添加Oculus API key**
1. 通过“菜单 -> Oculus -> Platform -> EditSettings”创建一个 OculusPlatformSettings 文件;
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052809.png">
	</div>
2. 找到并选中 Assets/Resources/ 下的 OculusPlatformSettings，点击图中的按键：“Create / Find your app on https://dashboard.oculus.com ”
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052810.png">
	</div>
3. 在弹出的网页上，登陆自己的 Oculus 开发者账号，然后点击 Create New App；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052811.png">
	</div>
4. 在弹出的平台选择窗口中，选择“Oculus Go & Gear VR”，目前还没有单独的 Quest 选项；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052812.png">
	</div>
5. 输入你的app名称，然后点击“保存并继续”；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052813.png">
	</div>
6. 复制App ID到OculusPlatform Settings的 Inspector界面中;
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052814.png">
	</div>
	在Application ID下的两个输入框( "Oculus Rift" and "Oculus Go/Quest or Gear VR")中都输入 App ID；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052815.png">
	</div>
7. 如果还报了一个"Please enter a valid user credentials"的错，取消勾选“Use Standalone Platform”即可；

**修改Oculus Platform Tool**
1. 通过“菜单 -> Oculus -> Tool -> Oculus Platform Tool”打开 Oculus Platform Tool面板；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052817.png">
	</div>
2. 将Target Oculus Platform 由原来的 GearVR or Go 改成 Oculus Quest；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052818.png">
	</div>


## C.对Unity进行设置
1. 安卓相关的设置：菜单 -> Edit -> Project Settings -> Player -> Settings For Android
	- **XR SEttings**: 勾选 Virtual Reality Supported，在 VirtualRealitySDKs 中添加Oculus
	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052805.png">
	</div>

	- **Other Settings**: 在Graphics APIs 中移除 Vulkan
	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052807.png">
	</div>

	- **Other Settings**: 找到Minimum API Level，修改成 Android 4.4 ‘KitKat’ (API Level 19)；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052808.png">
	</div>
2. 更改Unity的开发平台:菜单 -> File -> Build Settings 打开窗口，选择 Android 平台，将 Texture Compression 设置成 ASTC , 点击 Switch Platform 按键；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052816.png">
	</div>


## D.连接 Quest
通过手机的 Oculus app 可以将 Quest头显 设置成开发者模式（Developer Mode）

1. 确保你在 Quest头显 上登陆的账号与 手机Oculus App上的一致；
2. 按照App的提示配对你的Quest头显；	*需要注意的是，连接Wifi时，如果总是显示连接失败，需要切换到可以上外网的wifi；*
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/cellPhone/OculusQuest_phone_19052801.png">
	</div>
3. 选中你的Quest头显 -> 进入更多设置（More Settings) -> Developr Mode -> 打开
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/cellPhone/OculusQuest_phone_19052803.png">
	</div>
4. 通过USB将电脑和Quest连接在一起；第一次连接时需要带上头显，用手柄选择“允许电脑连接Quest”；
5. 连接完成后，可以在 Build Setting 中的 Run Device 找到对应的 Quest设备；(如果没有，点击Refresh试试)
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052819.png">
	</div>


### E.打包测试
将Assets/Oculus/VR/Scenes下的GearVrControllerTest场景添加到 Build Settings 中，点击Build And Run即可在Quest中运行；
如果出现下图表示安装成功；
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052820.png">
	</div>


最后吐槽一下Quest的账号管理方式，我在Quest系统中找了好久找不到退出登录的方法；后来在官网发现：如果要退出Quest上的账号，就需要恢复出厂设置。。。具体可以参考[Oculus官网的说明](https://support.oculus.com/263086061243965/)
 	<div align=center>
		<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/OculusQuest/OculusQuest_19052821.png">
	</div>



**致谢**：
本文主要参考自Daniel Leivers的博客：[How to get started with Oculus Quest and Unity on macOS](https://medium.com/@sofaracing/how-to-develop-for-oculus-quest-on-macos-with-unity-5aa487b80d13)
如果能上外网的同学也可以查看 [youtube上的一个视频](https://www.youtube.com/watch?v=eySe4Wj6xbk)



---
title: 基于SteamVR1.9.16，如何设置Tracker
date: 2019-12-31
tags: [HTCVive, SteamVR]
categories: VR开发
---

最近将SteamVR Runtime更新到1.9.16，结果发现它的操作界面又变了；
关于新版本Steam Rumtime的Tracker配对问题，很多人发现进到Demo，Tracker的朝向不对，跟现实的角度有一定差距，下面我们就来解决一下这个问题；

## Manage Controller Bingding的设置

1. 打开Steam应用；
<div align=center>
	<img width=100 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123101.png">
</div> 
2. 打开SteamVR Runtime；
<div align=center>
	<img width=500 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123102.png">
</div> 
3. 保证SteamVR正常运行中，并且配对好两个Tracker；
<div align=center>
	<img width=350 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123103.png">
</div>
4. 选择“设备”，再选择“控制器设置”；
<div align=center>
	<img width=350 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123104.png">
</div>
5. 选择“Controllers”，再选择“Manage Controller Bingding”；
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123105.png">
</div>
6. 找到“Manage Controller Bindings For”，并选择要运行的程序名称（也就是Tracker出现朝向问题的程序）；
<div align=center>
	<img width=300 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123106-7.png">
</div>
7. 将Active Controller Binding 设置成 “CUSTOM”，再选择“EDIT THIS BINDING”；
<div align=center>
	<img width=350 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123108.png">
</div>
8. 选择返回，返回上一级界面；
<div align=center>
	<img width=620 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123109.png">
</div>
9. 重新选择“当前控制器”；
<div align=center>
	<img width=500 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123110.png">
</div>
10. 将当前控制器设置成 “Vive Tracker in Hand”；
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123111.png">
</div>
11. 在当前按键设置中，选择“编辑”；
<div align=center>
	<img width=450 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123112.png">
</div>
12. 选择“编辑动作姿势”；
<div align=center>
	<img width=620 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123113.png">
</div>
13. 设置“左手原始”；
<div align=center>
	<img width=400 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123114.png">
</div>
14. 将左手原始，设置成 “left_pose”；
<div align=center>
	<img width=350 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123115.png">
</div>
15. 同理，将右手原始设置成“right_pose”;
<div align=center>
	<img width=250 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123116.png">
</div>
16. 关闭窗口，再返回上一级；
<div align=center>
	<img width=600 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123117.png">
</div>
17. 看到“当前按键设置”里面出来了（本地更改）模式即可；
<div align=center>
	<img width=600 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123118.png">
</div>
18. 关闭SteamVR；
<div align=center>
	<img width=350 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123119.png">
</div>
19. 完全退出Steam；（桌面菜单栏，找到Steam的图标，右键，退出）
<div align=center>
	<img width=380 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123120.png">
</div>
20. 重新启动Demo； 再重新打开SteamVR，不打开Steam即可；（注意，不打开Steam，只打开SteamVR；）


**注意**: 在运行Steam的时候，Tracker朝向还是有问题的，就是要单独打开SteamVR的情况才能使用，具体原因不明，等后面的SteamVR版本更新了之后应该会解决这个问题；


## Vive追踪器的设置

1. 在配对完Tracker后，右键Tracker图标，选择“管理Vive追踪器”；
<div align=center>
	<img width=350 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123121.png">
</div>
2. 找到对应的，已经识别到的，亮绿灯的Tracker设备，分别设置成“手持-左手”和“手持-右手”；
<div align=center>
	<img width=350 src="https://raw.githubusercontent.com/ckhongme/HexoBlog/master/source/images/VR%20Development/HTC%20Vive/SteamVR2.0/Rumtime1.9.16/SteamVR2.0_19123122.png">
</div>

**注意**: 关于区分左右手的问题，可以先关闭一个Tracker的电源，这时候打开Vive追踪器，当前的Tracker设备就是界面里亮绿灯的Tracker；
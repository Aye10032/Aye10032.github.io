---

layout: post

title: "WIN10关闭蓝牙耳机绝对音量功能"

date: 2020-12-21

categories: 
	- 教程
	- 日常

tag: 
	- 教程
	- 日常
typora-root-url: ..
---

# WIN10关闭蓝牙耳机绝对音量功能

<!-- more -->

通过执行以下命令来使用命令提示符启用或禁用绝对音量：

要禁用绝对音量功能，请执行：

```powershell
reg add HKLM\SYSTEM\ControlSet001\Control\Bluetooth\Audio\AVRCP\CT /v DisableAbsoluteVolume /t REG_DWORD /d 1 /f
```

要启用绝对音量功能，请执行以下操作：

```powershell
reg add HKLM\SYSTEM\ControlSet001\Control\Bluetooth\Audio\AVRCP\CT /v DisableAbsoluteVolume /t REG_DWORD /d 0 /f
```

重新启动Windows，以使注册表更改生效。
# Thinkpad-E470-OpenCore

联想Thinkpad-E470的黑苹果EFI，OpenCore版本0.7.5

参考教程：[OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)

## 电脑配置

- CPU: Intel i5 7200U
- iGPU: Intel HD Graphics 620
- dGPU: NVIDIA Geforce 920MX
- Audio: Intel HD Audio (Layout ID 15)
- LAN: RTL8111/8168/8411 Gigabit Ethernet Controller
- WIFI: QCA9377 802.11ac Wireless Network Adapter

| iGPU | dGPU |
| --- | --- |
| ![](https://github.com/hsinyuwang/Thinkpad-E470-OpenCore/blob/main/images/iGPU.PNG?raw=true) | ![](https://github.com/hsinyuwang/Thinkpad-E470-OpenCore/blob/main/images/dGPU.PNG?raw=true) |


## 已知问题

- 无线网卡不能正常使用，已替换为BCM94352Z
- dGPU已禁用，并自行编译了“SSDT-dGPU-Off.aml”用于关闭dGPU电源
- HDMI外接显示器紫屏

紫屏解决方案：

- 下载脚本[patch-edid.rb](https://github.com/hsinyuwang/Thinkpad-E470-OpenCore)
- 打开终端，cd到桌面，然后使用ruby命令再将脚本拖入终端回车；
- 桌面会生成显示器的edid文件；
- 右键点击访达，输入：/System/Library/Displays/Contents/Resources/Overrides/
- 将生成的文件拖入该文件夹重启即可。
  
**Mac 10.15注意事项**

> Mac OS 10.15系统版本开启了SIP系统完整性保护功能，系统文件夹是只有读权限的，无法将edid文件拖入系统文件夹,需要在恢复模式关闭SIP后再对系统文件读写。通过开机时按住 cmd+R 进入恢复模式。如果是黑苹果，在OpenCore引导界面，进入Recovery（恢复）模式。

在屏幕最上方的工具栏找到实用工具，打开终端，输入

```
csrutil disable
```

然后确认是否已经禁用

```
csrutil status
```

禁用系统防护（SIP）后，重启系统，打开终端，sudo su 并输入密码进入全局模式，然后输入

```
sudo mount -o rw / 
sudo cp -r '将桌面上的edid拖入终端' /System/Library/Displays/Contents/Resources/Overrides/
```

解决问题后，再次重启进入恢复模式，打开终端，输入

```
csrutil enable
```

## 使用须知
修改SMBIOS信息
- PlatformInfo -> Generic -> MLB
- PlatformInfo -> Generic -> SystemSerialNumber
- PlatformInfo -> Generic -> SystemUUID

## 测试环境

- macOS Catalina 10.15.7

## 效果展示

![](https://github.com/hsinyuwang/Thinkpad-E470-OpenCore/blob/main/images/demo.jpg?raw=true)

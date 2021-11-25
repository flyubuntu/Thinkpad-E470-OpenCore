# Thinkpad-E470-OpenCore

联想Thinkpad-E470的黑苹果EFI，OpenCore版本0.75

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

## 使用须知
修改SMBIOS信息
- PlatformInfo -> Generic -> MLB
- PlatformInfo -> Generic -> SystemSerialNumber
- PlatformInfo -> Generic -> SystemUUID

## 测试环境

- macOS Catalina 10.15.7

## 效果展示

![](https://github.com/hsinyuwang/Thinkpad-E470-OpenCore/blob/main/images/demo.jpg?raw=true)

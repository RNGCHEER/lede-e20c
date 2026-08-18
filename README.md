# RADXA E20C LEDE固件编译

本仓库使用GitHub Actions自动编译LEDE固件，针对RADXA E20C（瑞莎 E20C）设备。

## 设备简介

[RADXA E20C](https://docs.radxa.com/e/e20c/getting-started/introduction) 是一款基于Rockchip RK3528A的高性价比ARM开发板，支持eMMC存储和TF卡扩展，非常适合用作软路由、NAS或边缘计算设备。

## 硬件规格

| 参数 | 规格 |
|------|------|
| **型号** | 瑞莎 E20C |
| **SoC** | Rockchip RK3528A |
| **CPU** | 四核 ARM Cortex-A53 频率最高达 2.0GHz |
| **GPU** | ARM Mali-450 GPU，支持 OpenGL® ES1.1, ES2.0, OpenVG® 1.1 |
| **内存** | 1GB / 2GB / 4GB 32位 LPDDR4 |
| **存储** | 板载 eMMC: 0GB / 8GB / 16GB / 32GB / 64GB<br>microSD 存储卡 |
| **硬件编解码** | H.264、H.265 和 AVS2 解码，支持 4Kx2K@60fps<br>H.264 和 H.265 编码，支持 1920x1080@60fps |
| **以太网** | 2x 千兆以太网 |
| **USB** | 1x USB 2.0 端口 |
| **供电** | 仅支持 5V |
| **尺寸** | 66mm x 66mm |

## 固件功能

### 📡 代理工具

#### 🔹 PassWall（完整版）
- 支持所有代理协议：Shadowsocks/Rust、VMess、Trojan、VLESS、Hysteria、NaiveProxy、TUIC 等
- 核心组件：ipt2socks、dns2socks、tcping
- 透明代理 + TProxy 模式
- 多节点负载均衡
- 节点自动切换

#### 🔹 SmartDNS + ChinaDNS
- 国内外DNS智能分流
- DNS缓存加速
- 防止DNS污染和劫持

#### 🔹 OpenClash
- 基于Clash内核的透明代理
- 支持多种代理协议
- LuCI管理界面
- 订阅自动更新

### 💾 存储支持
- **eMMC写入**: 支持直接将固件写入板载eMMC（0/8/16/32/64GB可选）
- **TF卡启动**: 支持从microSD存储卡启动，便于测试和恢复
- **ext4文件系统**: 高性能读写支持

### 📱 4G/5G模组 & 安卓USB共享
- QMI/MBIM/NCM/PPP拨号协议
- RNDIS/NCM安卓USB网络共享
- 高通、华为、中兴等主流模组驱动

### 🐳 Docker支持
- Docker CE + CLI + Containerd
- LuCI Docker管理界面
- overlay2/bridge/host/ipvlan网络

## 使用方法

### 方法一：写入TF卡
1. 下载固件文件
2. 使用Balena Etcher或dd命令写入TF卡
3. 将TF卡插入E20C的microSD卡槽
4. 上电启动

### 方法二：写入eMMC
1. 先从TF卡启动
2. 使用`dd`命令将固件写入eMMC
3. 断电移除TF卡
4. 从eMMC启动

### 方法三：SSH网络安装
1. 通过网线连接E20C（双千兆以太网口任选其一）
2. 访问LuCI界面
3. 在系统-备份/升级中上传固件

## 固件编译

1. Fork本仓库
2. 在GitHub Actions页面触发编译
3. 编译完成后，在Actions的Artifacts或Releases页面下载固件

## 自定义配置

如需修改编译配置，编辑`config/E20C.config`文件。

## 相关资源

- [RADXA E20C官方文档](https://docs.radxa.com/e/e20c/getting-started/introduction)
- [RADXA E20C Wiki](https://wiki.radxa.com/Rock5/zh-cn/E20c)
- [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)
- [PassWall](https://github.com/xiaorouji/openwrt-passwall)
- [SmartDNS](https://github.com/pymumu/smartdns)
- [OpenClash](https://github.com/vernesong/OpenClash)

## 注意事项

1. 首次编译可能需要较长时间（约2-3小时）
2. eMMC版本需要使用官方工具预烧录TF卡镜像
3. 建议使用x86设备运行OpenClash以获得更好性能
4. 4G/5G模组需要在LuCI界面中进行配置
5. 供电仅支持5V，请使用合格的5V电源适配器
6. PassWall和OpenClash二选一使用，避免端口冲突

## 致谢

- [RADXA](https://www.radxa.com/) - E20C硬件设计
- [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede) - LEDE源码
- [xiaorouji/openwrt-passwall](https://github.com/xiaorouji/openwrt-passwall) - PassWall代理
- [pymumu/smartdns](https://github.com/pymumu/smartdns) - SmartDNS
- [OpenClash](https://github.com/vernesong/OpenClash) - 代理工具

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

### 🔐 KMS 激活服务
- **vlmcsd**: 支持 Windows/Office KMS 激活
- LuCI 管理界面
- 无需额外配置，开箱即用

### 🌐 DDNS 动态域名解析
- **支持服务商**:
  - Cloudflare
  - DNSPod
  - No-IP
  - 阿里云解析
- LuCI 管理界面
- 自动更新域名解析

### 📡 代理工具

#### 🔹 PassWall 1 + PassWall 2
- 支持所有代理协议：Shadowsocks/Rust、VMess、Trojan、VLESS、Hysteria2、NaiveProxy 等
- 透明代理 + TProxy 模式
- 多节点负载均衡

#### 🔹 SmartDNS + ChinaDNS
- 国内外DNS智能分流
- DNS缓存加速

#### 🔹 OpenClash
- 基于Clash内核的透明代理
- 支持多种代理协议

### 💾 存储支持
- **eMMC写入**: 支持直接将固件写入板载eMMC
- **TF卡启动**: 支持从microSD存储卡启动
- **ext4文件系统**: 高性能读写支持

### 📱 4G/5G模组 & 安卓USB共享
- QMI/MBIM/NCM/PPP拨号协议
- RNDIS/NCM安卓USB网络共享

### 🐳 Docker支持
- Docker CE + CLI + Containerd
- LuCI Docker管理界面

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
1. 通过网线连接E20C
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
- [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)
- [openwrt-passwall](https://github.com/Openwrt-Passwall/openwrt-passwall)
- [OpenClash](https://github.com/vernesong/OpenClash)

## 注意事项

1. 首次编译可能需要较长时间（约2-3小时）
2. 供电仅支持5V
3. PassWall和OpenClash二选一使用
4. KMS服务仅供学习测试使用

## 致谢

- [RADXA](https://www.radxa.com/) - E20C硬件设计
- [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede) - LEDE源码
- [Openwrt-Passwall](https://github.com/Openwrt-Passwall/openwrt-passwall) - PassWall代理
- [OpenClash](https://github.com/vernesong/OpenClash) - 代理工具

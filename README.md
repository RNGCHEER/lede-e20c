# LEDE固件编译 for E20C

本仓库使用GitHub Actions自动编译LEDE固件，针对GL-E20C设备，支持4G/5G模组、安卓USB网络共享、Docker和OpenClash。

## 功能特性

### 📡 4G/5G模组支持
- 支持多种4G/5G USB模组（高通、华为、中兴等）
- 支持QMI、MBIM、NCM、PPP等拨号方式
- 自动识别和配置移动网络

### 📱 安卓USB网络共享
- 支持安卓手机USB Tethering
- RNDIS/NCM网络协议支持
- 即插即用，无需额外配置

### 🐳 Docker支持
- 完整的Docker CE环境
- LuCI Docker管理界面
- 支持overlay2存储驱动
- 预配置bridge、host、ipvlan/macvlan网络

### 🔒 OpenClash支持
- 基于Clash的透明代理
- 支持多种代理协议
- LuCI管理界面
- 定时更新订阅

## 使用方法

1. Fork本仓库
2. 在GitHub Actions页面触发编译
3. 编译完成后，在Actions的Artifacts或Releases页面下载固件

## 固件说明

- 基于[coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)源码
- 针对GL-E20C设备优化
- 包含常用插件和功能
- 自动发布到GitHub Releases

## 自定义配置

如需修改编译配置，编辑`config/E20C.config`文件。

## 相关配置选项

### Docker相关
- `CONFIG_PACKAGE_docker-ce=y` - Docker引擎
- `CONFIG_PACKAGE_luci-app-dockerman=y` - Docker管理界面

### OpenClash相关
- `CONFIG_PACKAGE_luci-app-openclash=y` - OpenClash插件

### 4G/5G模组相关
- `CONFIG_PACKAGE_kmod-usb-net-qmi-wwan=y` - QMI协议支持
- `CONFIG_PACKAGE_kmod-usb-serial-option=y` - 串口模组支持

## 致谢

- [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)
- [haiibo/OpenWrt](https://github.com/haiibo/OpenWrt)
- [OpenClash](https://github.com/vernesong/OpenClash)

## 注意事项

1. 首次编译可能需要较长时间（约2-3小时）
2. Docker功能需要较大存储空间
3. 建议使用x86设备运行OpenClash以获得更好性能
4. 4G/5G模组需要在LuCI界面中进行配置

# LEDE固件编译 for E20C
# LEDE固件编译 for E20C

本仓库使用GitHub Actions自动编译LEDE固件，针对E20C设备。

## 使用方法

1. Fork本仓库
2. 在GitHub Actions页面触发编译
3. 编译完成后，在Actions的Artifacts中下载固件

## 固件说明

- 基于coolsnowwolf/lede源码
- 针对E20C设备优化
- 包含常用插件和功能

## 自定义配置

如需修改编译配置，编辑`config/E20C.config`文件。

## 致谢

- [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)
- [haiibo/OpenWrt](https://github.com/haiibo/OpenWrt)

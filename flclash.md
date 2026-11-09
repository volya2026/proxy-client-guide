---
title: "FlClash 下载与使用教程（2026）：官方安装包选择、导入订阅、安卓与电脑设置"
description: "FlClash 非官方中文教程：认准 chen08209/FlClash 官方渠道，按 Android、Windows、macOS、Linux 选对安装包，导入订阅、选择节点与出站模式，并说明系统代理、虚拟网卡和常见问题。"
permalink: /flclash/
---

# FlClash 下载与使用教程

文章最后更新：2026年11月9日（版本信息核对于同日，当前正式版为 v0.9.3）

FlClash 是一款基于 Mihomo（Clash Meta）内核的开源代理客户端，一个软件同时支持 Android、Windows、macOS 和 Linux，开源无广告。官方下载渠道只有两个：[GitHub Releases](https://github.com/chen08209/FlClash/releases) 和开发者的 [官方网站](https://chen08209.github.io/FlClash/zh/)。

> 本页是非官方中文教程，内容根据 [FlClash 官方仓库](https://github.com/chen08209/FlClash) 的说明和发布页整理。软件更新较快，界面和文件名以官方最新版本为准。

## 先认准官方渠道

搜索“FlClash 官网”时，会出现很多带 flclash 字样的第三方网站，还有不少别人修改过的版本。说白了，这些都不是官方发布的：

- 官方仓库：`github.com/chen08209/FlClash`
- 官方网站：`chen08209.github.io/FlClash`
- 安卓用户还可以使用官方的 F-Droid 仓库，入口在官方仓库说明页的“下载”部分

除此之外的“官网”、网盘和修改版，安装包来源无法核实，不建议下载。

## 安装包怎么选

打开 [GitHub Releases](https://github.com/chen08209/FlClash/releases)，找到标着 Latest 的正式版，在 Assets 里按下表选择。不想自己选的话，打开 [官方网站](https://chen08209.github.io/FlClash/zh/) 的下载区，它会根据你的设备自动选好安装包。

| 你的设备 | 选择的安装包（以 v0.9.3 为例） | 说明 |
|--|--|--|
| 安卓手机（绝大多数） | `FlClash-0.9.3-android-arm64-v8a.apk` | 不确定就选这个 |
| 较老的 32 位安卓手机 | `FlClash-0.9.3-android-armeabi-v7a.apk` | arm64 装不上时再试 |
| 安卓模拟器 / x86 设备 | `FlClash-0.9.3-android-x86_64.apk` | 普通手机用不到 |
| Windows 10 及以上，普通电脑 | `FlClash-0.9.3-windows-amd64-setup.exe` | 安装版 |
| Windows，想用免安装版 | `FlClash-0.9.3-windows-amd64.zip` | 便携版，解压即用 |
| Windows，骁龙等 ARM 笔记本 | `FlClash-0.9.3-windows-arm64-setup.exe` | 只有 ARM 设备才选 |
| macOS 12 及以上，Apple M 芯片 | `FlClash-0.9.3-macos-arm64.dmg` | |
| macOS 12 及以上，Intel 芯片 | `FlClash-0.9.3-macos-amd64.dmg` | |
| Debian / Ubuntu | `FlClash-0.9.3-linux-amd64.deb` | ARM 设备选 `arm64.deb` |
| Fedora 等 | `FlClash-0.9.3-linux-amd64.rpm` | ARM 设备选 `arm64.rpm` |
| 其他 Linux | `FlClash-0.9.3-linux-amd64.AppImage` | ARM 设备选 `arm64.AppImage` |

文件名中的版本号会随更新变化，只看后缀就行。`SHA256SUMS` 是校验文件，不是安装包。

## 安装步骤

### Android

1. 下载对应的 `.apk` 文件。
2. 打开安装包，如果系统提示“禁止安装未知来源应用”，按提示允许浏览器或文件管理器安装应用。
3. 安装完成后打开 FlClash。

### Windows

1. 安装版：双击 `setup.exe`，按提示完成安装。
2. 便携版：把 `.zip` 解压到一个固定的文件夹，运行里面的 FlClash 即可。

### macOS

1. 按芯片类型下载 `.dmg` 文件（在“关于本机”里可以看到是 Apple M 芯片还是 Intel）。
2. 打开 `.dmg`，把 FlClash 拖进“应用程序”文件夹。
3. 也可以用 Homebrew 安装：

```
brew tap chen08209/tap
brew install --cask flclash
```

### Linux

`.deb` 安装包会自动安装所需依赖。使用 AppImage 或 `.rpm` 时，需要先安装 AyatanaAppIndicator 库，托盘图标才能显示：

```
sudo apt-get install libayatana-appindicator3-1   # Debian 与 Ubuntu
sudo dnf install libayatana-appindicator-gtk3     # Fedora
```

### 首次打开：确认免责声明

第一次打开 FlClash 时，需要先确认免责声明，之后才能正常使用：

1. 读完声明后，点击右下角的“同意”。
2. 弹出“复述声明”窗口，把框里那段话完整输入到下方的输入框里。
3. 点击“确定”，进入仪表盘。

![FlClash 首次打开的免责声明：点击“同意”，在“复述声明”输入框中完整输入声明，再点“确定”]({{ '/assets/flclash/flclash-01-disclaimer.png' | relative_url }})

## 导入订阅

FlClash 本身不提供节点，需要导入你的订阅链接才能使用。

1. 在订阅服务的用户中心复制 Clash 订阅链接。
2. 打开 FlClash，进入“配置”页面，点击“添加配置”（已经有配置时，按钮在右上角的加号）。
3. 选择“链接”，把订阅链接粘贴到“链接”一栏，点击“提交”。

![FlClash 配置页面：点击左侧“配置”，在“添加配置”菜单里选择“链接”]({{ '/assets/flclash/flclash-02-add-profile.png' | relative_url }})

![FlClash 从链接导入窗口：把订阅链接粘贴到“链接”一栏，点击“提交”]({{ '/assets/flclash/flclash-03-import-url.png' | relative_url }})

4. 导入完成后，配置卡片右侧出现蓝色勾，表示已经选中。卡片上还能看到已用流量和到期日期，左侧菜单也会多出“代理”页面。

![FlClash 导入成功后的配置卡片，显示已用流量、到期日期和选中标记]({{ '/assets/flclash/flclash-04-profile-card.png' | relative_url }})

除了链接，“添加配置”里还可以选择“二维码”和“文件”导入。手机上用“二维码”扫一下服务商后台的订阅二维码，比手动粘贴更省事。

如果服务商后台有“一键导入 Clash”按钮，在已经安装 FlClash 的设备上点它，也可以直接导入。FlClash 支持 `clash://`、`clashmeta://` 和 `flclash://` 开头的导入链接。

还没有 Clash 订阅的话，可以参考这份 [Clash 节点购买推荐](https://tuijianvpn.com/4191)，先选一家支持 Clash 订阅的服务，建议从月付开始试用。

## 选择节点与出站模式

进入“代理”页面，可以看到订阅里的策略组。展开“节点选择”这类策略组，点击闪电图标（延迟测试）测一下各节点延迟，再点一个延迟正常的节点，出现蓝色勾就是选中了。

![FlClash 代理页面：点击“代理”，用闪电图标做延迟测试，再点选一个节点]({{ '/assets/flclash/flclash-05-select-node.png' | relative_url }})

节点名称里常见 `0.5x`、`1x`、`2x` 这样的标记，代表节点倍率，也就是用这个节点时套餐流量的扣除倍数。具体怎么算，可以看这篇 [节点倍率是什么意思](https://tuijianvpn.com/9231)。

“出站模式”在仪表盘上切换，有三种：

| 模式 | 流量怎么走 | 适合场景 |
|--|--|--|
| 规则 | 按订阅里的规则自动分流，国内网站直连，国外网站走节点 | 日常使用，推荐默认选这个 |
| 全局 | 所有流量都走你选中的节点 | 临时排查某个网站是否被规则误判 |
| 直连 | 所有流量都不走代理 | 临时关掉代理但不想退出软件 |

## 启动连接：安卓和电脑不一样

### Android

回到“仪表盘”，点击“启动”。第一次启动时，系统会弹出 VPN 连接请求，点“确定”允许即可。之后通知栏会显示 FlClash 正在运行。

如果只想让部分应用走代理，可以在“访问控制”中设置：白名单模式只让选中的应用走代理，黑名单模式把选中的应用排除在外。

### Windows / macOS / Linux

回到“仪表盘”，点击状态卡片右侧的启动按钮，状态变成“运行中”后，确认仪表盘上的“系统代理”或“虚拟网卡”其中一个开关已经打开：

![FlClash 电脑版仪表盘：启动按钮、出站模式，以及系统代理和虚拟网卡两个开关]({{ '/assets/flclash/flclash-06-dashboard.png' | relative_url }})

| 对比项 | 系统代理 | 虚拟网卡（TUN） |
|--|--|--|
| 原理 | 修改系统的代理设置，应用自己决定是否遵守 | 创建一张虚拟网卡，接管系统流量 |
| 覆盖范围 | 浏览器和大多数遵守系统代理的软件 | 包括不遵守系统代理的软件，比如游戏、命令行 |
| 使用门槛 | 打开开关即可 | 需要管理员权限，开启时按提示授权 |

简单来说：只是浏览网页，开系统代理就够了；遇到某些软件不走代理，再开虚拟网卡。

## 怎么确认已经连上

- 仪表盘状态显示“运行中”，安卓通知栏能看到 FlClash 的连接通知。
- 在“代理”页面，当前节点有正常的延迟数值，而不是失败或超时。
- 用浏览器打开一个国外网站，能正常加载。

## 常见问题

### 安卓应该下载哪个 APK

绝大多数手机选 `arm64-v8a`。只有很老的 32 位手机才需要 `armeabi-v7a`，`x86_64` 一般只用于模拟器。

### 订阅导入失败怎么办

- 提示“不是有效的订阅链接或代理分享链接”时，检查链接是否复制完整，有没有多出空格或换行。
- 订阅链接要以 `http://` 或 `https://` 开头。
- 在订阅服务的用户中心重置一次订阅链接，再重新导入。

### 电脑上打不开虚拟网卡

软件里的提示是“虚拟网卡仅在管理员模式生效”。开启时请按系统提示授权管理员权限；暂时无法授权的话，可以先用系统代理。

### Linux 上看不到托盘图标

使用 AppImage 或 `.rpm` 时，需要先安装 AyatanaAppIndicator 库，命令见上文 Linux 安装部分。

### FlClash 和 Clash Verge Rev 有什么区别

两者都基于 Mihomo 内核，订阅链接可以通用。主要区别是 FlClash 同时支持安卓和电脑，手机和电脑可以用同一套软件；Clash Verge Rev 只支持电脑端，设置项更偏桌面用户。只在电脑上使用的话，也可以看这篇 [Clash Verge Rev 下载与使用教程](https://volya2026.github.io/proxy-client-guide/clash-verge-rev/)。

### 第三方修改版能用吗

GitHub 上有不少基于 FlClash 修改的版本，它们不是官方发布的，更新和安全性无法保证。建议只从官方渠道下载。

## 相关链接

- [FlClash 官方仓库](https://github.com/chen08209/FlClash)
- [FlClash 更新日志](https://github.com/chen08209/FlClash/blob/main/CHANGELOG.md)
- [代理客户端下载与配置教程索引](https://volya2026.github.io/proxy-client-guide/)

---

由 [推荐VPN](https://tuijianvpn.com/) 整理。本页与 FlClash 官方无关，如有错误欢迎提 Issue 指出。

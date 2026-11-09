---
title: "Clash Meta for Android 下载与使用教程（2026）：安卓 APK 选择、导入订阅与常见问题"
description: "Clash Meta for Android（CMFA）非官方中文教程：认准官方下载渠道，选对 APK，导入订阅、选择节点并开启 VPN，附常见问题。"
permalink: /clash-meta-for-android/
---

# Clash Meta for Android 下载与使用教程

文章最后更新：2026年11月9日（版本信息核对于2026年11月8日，当前正式版为 v2.11.36）

Clash Meta for Android（简称 CMFA）是 Mihomo（Clash Meta）内核的安卓图形客户端，由 MetaCubeX 团队维护，开源免费。官方下载渠道只有两个：[GitHub Releases](https://github.com/MetaCubeX/ClashMetaForAndroid/releases) 和 [F-Droid](https://f-droid.org/packages/com.github.metacubex.clash.meta/)。

> 本页是非官方中文教程，内容根据 [CMFA 官方仓库](https://github.com/MetaCubeX/ClashMetaForAndroid) 的说明和发布页整理。界面文字以软件简体中文版为准，更新后可能略有变化。文中截图来自 Android 7.0 环境下的 CMFA v2.11.36，使用的是演示订阅，节点名称和延迟数字仅作示意，链接已打码。电脑端用户可以看 [Clash Verge Rev 下载与使用教程](https://volya2026.github.io/proxy-client-guide/clash-verge-rev/)。

## 先认准官方版本

很多人搜的是“Clash for Android”。原版 Clash for Android 早已停止更新，它的官方仓库现在也已经不存在了。网上还能下到的同名 APK，大多是第三方重新打包的，来源无法核实。

现在安卓上的主流选择是 CMFA，它延续了原版的界面和用法，同时换成了仍在更新的 Mihomo 内核。认准下面两个地方下载：

- GitHub 仓库：`github.com/MetaCubeX/ClashMetaForAndroid`
- F-Droid 应用页，包名是 `com.github.metacubex.clash.meta`

其他网站上的“Clash Meta 官网”、网盘分享和修改版，都不建议下载。

## APK 怎么选

打开 [GitHub Releases](https://github.com/MetaCubeX/ClashMetaForAndroid/releases)，找到标着 Latest 的正式版。不要选标着 Pre-release 的测试版。然后在 Assets 里按下表选择：

| 你的设备 | 选择的安装包（以 v2.11.36 为例） | 说明 |
|--|--|--|
| 绝大多数安卓手机 | `cmfa-2.11.36-meta-arm64-v8a-release.apk` | 近几年的手机都选这个 |
| 不确定手机型号 | `cmfa-2.11.36-meta-universal-release.apk` | 通用版，所有架构都能装，文件更大 |
| 较老的 32 位手机 | `cmfa-2.11.36-meta-armeabi-v7a-release.apk` | arm64 装不上时再试 |
| 模拟器 / x86 设备 | `cmfa-2.11.36-meta-x86_64-release.apk` 或 `x86` | 普通手机用不到 |

版本号会随更新变化，只看 `arm64-v8a`、`universal` 这些标记就行。`output-metadata.json` 不是安装包，不用下载。

系统要求：最低 Android 5.0，官方推荐 Android 7.0 及以上。

## 安装

1. 用手机浏览器下载 APK。
2. 打开安装包。如果系统提示“禁止安装未知来源应用”，按提示允许浏览器或文件管理器安装应用。
3. 安装完成后打开 Clash Meta for Android。首页能看到“已停止”和“点此启动”，就说明装好了。

## 导入订阅

CMFA 本身不提供节点，需要导入你的 Clash 订阅链接才能使用。

1. 在订阅服务的用户中心复制 Clash 订阅链接。
2. 在 CMFA 首页点击“配置”，再点右上角的加号。

![CMFA 首页，点击配置]({{ '/assets/clash-meta-for-android/clash-meta-for-android-01-home.png' | relative_url }})

3. 在“创建配置”里选择“URL（从 URL 导入）”。

![创建配置页面，选择从 URL 导入]({{ '/assets/clash-meta-for-android/clash-meta-for-android-02-new-profile.png' | relative_url }})

4. 依次点每一项，在弹出的输入框里填写后点“确认”：
   - 名称：随便填，方便自己识别。
   - URL：粘贴订阅链接。
   - Age 私钥：标着“可选”，普通订阅留空即可。
   - 自动更新：建议填 1440（分钟），也就是每天更新一次。最少 15 分钟，不填就不自动更新。
5. 点右上角的“保存”图标（软盘形状），等“正在校验”提示消失。

![填写订阅链接和自动更新间隔后保存]({{ '/assets/clash-meta-for-android/clash-meta-for-android-03-import-url.png' | relative_url }})

6. 回到配置列表，点配置卡片左侧的圆圈选中它。卡片上能看到已用流量、总流量和到期时间。

![在配置列表中选中刚导入的订阅]({{ '/assets/clash-meta-for-android/clash-meta-for-android-04-select-profile.png' | relative_url }})

7. 按返回键回到首页，“配置”一栏显示“（你的配置名） 已激活”就可以了。

其他导入方式：“从文件导入”适合手里只有 `.yaml` 配置文件的情况；“从二维码导入”可以扫服务商后台的订阅二维码；如果服务商后台有“一键导入 Clash”按钮，在装好 CMFA 的手机上点它就能直接导入。CMFA 支持 `clash://` 和 `clashmeta://` 开头的导入链接。

还没有 Clash 订阅的话，可以参考这份 [Clash 节点购买推荐](https://tuijianvpn.com/4191)，先选一家支持 Clash 订阅的服务，建议从月付开始试用。

## 启动连接

1. 回到首页，点“点此启动”。
2. 第一次启动时，系统会弹出“网络连接请求”，点“确定”允许。不同安卓版本的弹窗文字略有差别。

![系统弹出网络连接请求，点确定]({{ '/assets/clash-meta-for-android/clash-meta-for-android-05-vpn-request.png' | relative_url }})

3. 首页状态变成“运行中”，并显示已转发的流量，就说明已经启动了。启动后首页会多出“代理”一栏。

![启动后首页显示运行中和代理入口]({{ '/assets/clash-meta-for-android/clash-meta-for-android-06-running.png' | relative_url }})

## 选择节点与模式

在首页点击“代理”（启动后才会出现），顶部标签是订阅里的各个策略组，下面是组里的节点。

- 先切到“节点选择”这类手动选择的组，点右下角的圆形闪电按钮做一次延迟测试，节点右侧会显示延迟数字。然后点一个延迟正常的节点，选中后卡片会变成深色。

![代理页面：延迟测试并选择节点]({{ '/assets/clash-meta-for-android/clash-meta-for-android-07-delay-test.png' | relative_url }})

- 右上角三点菜单 → “模式”里有不修改、直连模式、全局模式和规则模式。“不修改”就是沿用订阅里设定的模式。这里切换的模式只在本次运行中有效。

![右上角菜单里切换代理模式]({{ '/assets/clash-meta-for-android/clash-meta-for-android-08-mode.png' | relative_url }})

| 模式 | 流量怎么走 | 适合场景 |
|--|--|--|
| 规则模式 | 按订阅里的规则自动分流，国内网站直连，国外网站走节点 | 日常使用，推荐默认 |
| 全局模式 | 所有流量都走你选中的节点 | 临时排查某个网站是否被规则误判 |
| 直连模式 | 所有流量都不走代理 | 临时关掉代理但不想停止服务 |

订阅里的节点通常分为直连、中转、专线几种线路，稳定性和价格差别很大。想弄明白可以看这篇 [直连、中转、专线机场有什么区别](https://tuijianvpn.com/9196)。

## 让部分应用不走代理

默认情况下，所有应用都会走 CMFA。如果想让银行、支付这类应用直接连接，可以这样设置：

1. 首页 → “设置” → “网络”。
2. 在“访问控制模式”里选择：
   - 允许所有应用：默认，全部走代理。
   - 仅允许已选择的应用：只有选中的应用走代理。
   - 不允许已选择的应用：选中的应用不走代理。
3. 在“访问控制应用包列表”里勾选应用。

部分网络设置在 Clash 运行时不能修改，需要先停止服务，改完再启动。

## 怎么确认已经连上

- 首页显示“运行中”，通知栏有 Clash Meta for Android 的常驻通知。
- “代理”页面里，当前节点有正常的延迟数值。
- 用手机浏览器打开一个国外网站，能正常加载。

## 常见问题

### 下载哪个 APK

绝大多数手机选 `arm64-v8a`。实在不确定就选 `universal`，它兼容所有架构，只是文件大一些。

### 打开提示“应用损坏”或缺少运行组件

这通常是 APK 没下载完整。按上表重新从 GitHub Releases 下载对应的安装包，覆盖安装即可。

### 订阅导入失败

- 检查链接是否复制完整，有没有多出空格或换行。
- URL 只接受 `http(s)` 开头的链接。
- 在订阅服务的用户中心重置一次订阅链接，再重新导入。

### 怎么更新订阅里的节点

在“配置”页面，点某个配置右侧的三点菜单，选“更新”；点右上角的同步图标，可以一次更新全部配置。也可以在导入时设置自动更新间隔，这样就不用每次手动操作。

### 升级后配置不见了或要求重新保存

升级大版本后，软件可能会提示“设置已被清除，旧的配置文件需要再次保存”。进入“配置”，打开原来的配置再保存一次就行；如果还是不行，重新导入订阅。

### 已经连上了，但网页打不开

先在“代理”页面做一次延迟测试，换一个延迟正常的节点。还是不行的话，回到“配置”更新一次订阅，节点可能已经变了。

### 和 FlClash 有什么区别

两者都基于 Mihomo 内核，订阅链接可以通用。CMFA 只做安卓端，设置项更细；FlClash 同时支持安卓和电脑，手机和电脑可以用同一套软件。想统一用一个软件的话，可以看这篇 [FlClash 下载与使用教程](https://volya2026.github.io/proxy-client-guide/flclash/)。

### 能装在安卓电视上吗

官方没有单独的电视版。电视盒子一般可以安装 `universal` 或 `arm64-v8a` 版本，但界面是为手机设计的，用遥控器操作可能不太方便。

## 相关链接

- [Clash Meta for Android 官方仓库](https://github.com/MetaCubeX/ClashMetaForAndroid)
- [CMFA 的 F-Droid 页面](https://f-droid.org/packages/com.github.metacubex.clash.meta/)
- [代理客户端下载与配置教程索引](https://volya2026.github.io/proxy-client-guide/)

---

由 [推荐VPN](https://tuijianvpn.com/) 整理。本页与 Clash Meta for Android 官方无关，如有错误欢迎提 Issue 指出。

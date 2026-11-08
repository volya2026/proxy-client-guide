---
title: "Clash Verge Rev 下载与使用教程（2026）：安装、导入订阅、系统代理与 TUN 模式"
description: "Clash Verge Rev 非官方中文教程：只从官方 GitHub Releases 下载，按系统和芯片选对安装包，导入订阅、选择规则/全局/直连模式，并说明系统代理与 TUN 模式的区别和常见报错处理。"
permalink: /clash-verge-rev/
---

# Clash Verge Rev 下载与使用教程

文章最后更新：2026年11月7日（版本信息核对于同日，当前正式版为 v2.5.10）

Clash Verge Rev 是一款基于 Mihomo（Clash Meta）内核的开源桌面代理客户端，支持 Windows、macOS 和 Linux。它只通过官方 GitHub Releases 发布，下载请认准 [clash-verge-rev/clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev/releases)，其他自称“官网”的下载站都不是官方渠道。

> 本页是非官方中文教程，内容根据 [官方文档](https://www.clashverge.dev/) 和官方发布页整理。软件版本更新较快，界面和文件名以官方最新发布为准。

## Clash Verge Rev 和 Clash for Windows、原版 Clash Verge 是什么关系

- **Clash for Windows（CFW）**：2023 年 11 月 2 日宣布停止更新并删除了发布仓库，之后不会再有安全更新，不建议继续使用。
- **原版 Clash Verge**：原作者的仓库已归档停更。
- **Clash Verge Rev**：在原版 Clash Verge 基础上继续维护的版本，内核换成了开源的 Mihomo，目前仍在持续更新。

说白了，如果你以前用 CFW 或原版 Clash Verge，现在在电脑上换成 Clash Verge Rev 就行，订阅链接一般可以直接沿用。

## 官方下载地址与安装包怎么选

下载地址：[Clash Verge Rev GitHub Releases](https://github.com/clash-verge-rev/clash-verge-rev/releases)

打开后找到标着 Latest 的正式版，在 Assets 里按下表选择。文件名中的版本号会随更新变化，只看后缀就行。

| 你的系统 | 选择的安装包（以 v2.5.10 为例） | 说明 |
|--|--|--|
| Windows 10/11，普通电脑 | `Clash.Verge_2.5.10_x64-setup.exe` | 大多数 Windows 电脑选这个 |
| Windows，ARM 芯片电脑 | `Clash.Verge_2.5.10_arm64-setup.exe` | 只有确认是 ARM 设备才选 |
| Windows，打不开界面或缺少 WebView2 | `Clash.Verge_2.5.10_x64_fixed_webview2-setup.exe` | 内置 WebView2，体积更大，普通电脑不用选 |
| macOS，Apple M 系列芯片 | `Clash.Verge_2.5.10_aarch64.dmg` | 需要 macOS 12 及以上 |
| macOS，Intel 芯片 | `Clash.Verge_2.5.10_x64.dmg` | 需要 macOS 12 及以上 |
| Debian / Ubuntu / Deepin | `Clash.Verge_2.5.10_amd64.deb` | ARM 设备选 `arm64.deb` 或 `armhf.deb` |
| Fedora / CentOS / SUSE | `Clash.Verge-2.5.10-1.x86_64.rpm` | ARM 设备选 `aarch64.rpm` 或 `armhfp.rpm` |

需要注意的是：

- **不支持 Windows 7**。Win7 用户需要先升级到 Win10/11。
- 不确定 Windows 电脑是什么架构时，选 `x64`。
- 文件名带 `.sig` 的是签名校验文件，不是安装包，不用下载。

## 安装步骤

### Windows

1. 双击下载好的 `setup.exe`，按提示完成安装。
2. 也可以用 Windows 自带的包管理器 WinGet 安装：

```
winget install ClashVergeRev.ClashVergeRev
```

3. 需要便携版或修改配置目录的用户，可以用社区维护的 Scoop 渠道（官方不为这类下游渠道提供支持）：

```
scoop bucket add extras
scoop install extras/clash-verge-rev
```

如果安装后能看到托盘图标，但点开没有界面，多半是系统缺少 WebView2，可以先安装 WebView2，或者改用带 `fixed_webview2` 的安装包。

### macOS

1. 按芯片类型下载对应的 `.dmg` 文件（在“关于本机”里可以看到是 Apple M 芯片还是 Intel）。
2. 打开 `.dmg`，把 Clash Verge 拖进“应用程序”文件夹。
3. 升级新版本前，先在菜单栏图标里彻底退出旧版本，否则可能导致软件包损坏。

### Linux

下载 `.deb` 包后：

```
sudo apt install -y ./Clash.Verge_x.x.x_amd64.deb
```

下载 `.rpm` 包后：

```
sudo dnf install ./Clash.Verge-x.x.x-1.x86_64.rpm
```

Arch Linux 用户可以通过 AUR 安装 `clash-verge-rev-bin`。

## 导入订阅

Clash Verge Rev 本身不提供节点，需要导入你的订阅链接才能使用。

1. 在订阅服务的用户中心复制 Clash 订阅链接。
2. 打开 Clash Verge Rev，点击左侧“订阅”。
3. 把链接粘贴到顶部的“订阅文件链接”输入框，点击“导入”。
4. 导入成功后，订阅会以卡片形式出现，点击这张卡片启用它。

链接必须以 `http://` 或 `https://` 开头。导入失败时，可以看下文的常见问题。

还没有 Clash 订阅的话，可以参考这份 [Clash 节点购买推荐](https://tuijianvpn.com/4191)，先选一家支持 Clash 订阅的服务，建议从月付开始试用。

## 选择节点与代理模式

点击左侧“代理”，可以看到订阅里的节点分组。点击“延迟测试”可以测出各节点的延迟，然后手动选择一个节点。

页面顶部有三种代理模式：

| 模式 | 流量怎么走 | 适合场景 |
|--|--|--|
| 规则 | 按订阅里的规则自动分流，国内网站直连，国外网站走节点 | 日常使用，推荐默认选这个 |
| 全局 | 所有流量都走你手动选的节点 | 临时排查某个网站是否被规则误判 |
| 直连 | 所有流量都不走代理 | 临时关掉代理但不想退出软件 |

节点名称里经常能看到“中转”“专线”“IPLC”等字样，代表不同的线路类型，价格和稳定性也有差别。想弄清楚它们的区别，可以看这篇 [直连、中转、专线机场的区别](https://tuijianvpn.com/9196)。

## 系统代理和 TUN 模式怎么选

选好节点后，还要打开“系统代理”或“虚拟网卡模式”（TUN 模式）其中一个，流量才会真正交给 Clash Verge Rev 处理。两个开关在首页和“设置”里都能找到。

| 对比项 | 系统代理 | TUN 模式（虚拟网卡模式） |
|--|--|--|
| 原理 | 修改系统的代理设置，应用自己决定是否遵守 | 创建一张虚拟网卡，接管系统所有流量 |
| 覆盖范围 | 浏览器和大多数遵守系统代理的软件 | 包括不遵守系统代理的软件，比如游戏、命令行 |
| UDP 流量 | 不支持 | 支持 |
| 使用门槛 | 打开开关即可 | 需要先安装服务模式，或以管理员身份运行 |

简单来说：只是浏览网页，开系统代理就够了；游戏、命令行或某些软件不走代理时，再开 TUN 模式。开启 TUN 时不需要同时打开系统代理。

开启 TUN 的步骤：

1. 进入“设置”，在虚拟网卡模式旁点击“安装服务”，按提示允许管理员授权。
2. 首页显示“服务模式”后，打开“虚拟网卡模式”开关。
3. 如果不想安装服务，也可以直接以管理员身份运行 Clash Verge Rev 来使用 TUN。

## 怎么确认已经连上

- 首页提示“系统代理已启用”或“TUN 模式已启用”。
- 在“代理”页面，当前节点有正常的延迟数值，而不是超时。
- 用浏览器打开一个国外网站，能正常加载。

## 常见问题

### 订阅导入失败怎么办

- 提示 `client error(Connect)`：换一种导入方式，在订阅页面新建一个远程订阅配置，再粘贴链接；仍然失败时可以勾选“允许无效证书（危险）”后重试。
- 提示 401：在“设置”里打开“配置目录”，删除里面的文件后重启软件；仍不行就卸载旧版本后重新安装。
- 也可以先确认订阅链接本身是否有效，比如在订阅服务的用户中心重置一次链接。

### Windows 提示“此应用无法在你的电脑上运行”

基本是下错了安装包。大多数电脑应该下载 `x64` 版本，而不是 `arm64` 版本。

### 打开后没有界面，只有托盘图标

Clash Verge Rev 依赖 WebView2。检查是否用第三方软件禁用了 Edge 或 WebView2；如果已经卸载，重新安装 WebView2；仍然不行，就改用带 `fixed_webview2` 的安装包。

### 软件闪退或服务模式装不上

360、金山毒霸等安全软件可能拦截服务模式的安装。可以把 Clash Verge Rev 加入白名单，或者暂时关闭这类软件后再安装服务。

### 关掉 Clash Verge Rev 之后上不了网

通常是异常退出后系统代理没有被关闭。在 Windows 中打开“设置 → 网络和 Internet → 代理”，关闭“使用代理服务器”即可。

### 国内网站能打开，国外网站打不开

先确认当前选中的节点延迟正常，代理模式是“规则”或“全局”。如果节点正常却仍然打不开，可能是其他程序占用了默认代理端口 7897，或者用过的加速器改动了系统 hosts 文件，可以检查并删除异常条目。

### 开启 TUN 后网络异常

系统里可能有多余的网卡与规则冲突。可以在网络设置中删除不用的虚拟网卡后再试。

### macOS 提示软件包损坏

常见原因是旧版本还在运行时安装了新版本。彻底退出并卸载 Clash Verge Rev，删除相关文件后重新安装。

### 支持 Windows 7 吗

不支持。当前版本需要 Windows 10/11。

## 相关教程

- [Clash Verge Rev 官方文档](https://www.clashverge.dev/)
- [Clash Verge Rev 官方常见问题（Windows）](https://www.clashverge.dev/faq/windows.html)

---

由 [推荐VPN](https://tuijianvpn.com/) 整理。本页与 Clash Verge Rev 官方无关，如有错误欢迎提 Issue 指出。

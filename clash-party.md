---
title: "Clash Party（原 Mihomo Party）下载与使用教程（2026）：安装包选择、导入订阅与常见问题"
description: "Clash Party 就是原来的 Mihomo Party。非官方中文教程：认准官方渠道，按 Windows、macOS、Linux 选对安装包，导入订阅、选择节点并开启代理，附常见问题。"
permalink: /clash-party/
---

# Clash Party（原 Mihomo Party）下载与使用教程

文章最后更新：2026年11月8日（版本信息核对于同日，当前正式版为 v2.0.4）

Clash Party 是一款基于 Mihomo（Clash Meta）内核的电脑端代理客户端，支持 Windows、macOS 和 Linux，开源免费。官方下载渠道是 [GitHub Releases](https://github.com/mihomo-party-org/clash-party/releases)，官方网站是 [clashparty.org](https://clashparty.org/)。

> 本页是非官方中文教程，内容根据 [Clash Party 官方仓库](https://github.com/mihomo-party-org/clash-party) 的发布说明和官方文档整理。界面文字以软件简体中文版为准，更新后可能略有变化。安卓用户可以看 [Clash Meta for Android 下载与使用教程](https://volya2026.github.io/proxy-client-guide/clash-meta-for-android/)。

## Mihomo Party 和 Clash Party 是什么关系

两者是同一个软件。官方从 v1.8.6 版本（2025 年 8 月）开始，把软件名称从 Mihomo Party 改成了 Clash Party，仓库、开发团队和功能都延续了下来。

所以如果你看到旧教程里写的是 Mihomo Party，直接下载 Clash Party 就行，用法基本一样。

## 先认准官方渠道

- GitHub 仓库：`github.com/mihomo-party-org/clash-party`
- 官方网站：`clashparty.org`

其他自称“Mihomo Party 官网”的网站，以及网盘里的安装包，来源都无法核实，不建议下载。GitHub 上还有一些名字相近的安卓版项目，它们不是这个官方项目发布的。

## 安装包怎么选

打开 [GitHub Releases](https://github.com/mihomo-party-org/clash-party/releases)，找到标着 Latest 的正式版，在 Assets 里按下表选择：

| 你的系统 | 选择的安装包（以 v2.0.4 为例） | 说明 |
|--|--|--|
| Windows 10 / 11，普通电脑 | `clash-party-windows-2.0.4-x64-setup.exe` | 安装版，大多数人选这个 |
| Windows 10 / 11，想用免安装版 | `clash-party-windows-2.0.4-x64-portable.7z` | 便携版，解压即用 |
| Windows 10 / 11，骁龙等 ARM 笔记本 | `clash-party-windows-2.0.4-arm64-setup.exe` | 只有 ARM 设备才选 |
| Windows 7 / 8 | `clash-party-win7-2.0.4-x64-setup.exe` | 32 位系统选 `ia32` |
| macOS 11 及以上，Apple M 芯片 | `clash-party-macos-2.0.4-arm64.pkg` | |
| macOS 11 及以上，Intel 芯片 | `clash-party-macos-2.0.4-x64.pkg` | |
| macOS 10.15 | `clash-party-catalina-2.0.4-x64.pkg` | 专为老版本系统准备 |
| Debian / Ubuntu | `clash-party-linux-2.0.4-amd64.deb` | ARM 设备选 `arm64.deb` |
| Fedora 等 | `clash-party-linux-2.0.4-x86_64.rpm` | ARM 设备选 `aarch64.rpm` |
| Arch 系 | `clash-party-linux-2.0.4-x64.pkg.tar.zst` | 也可以从 AUR 安装 |

几点说明：

- Releases 里同时有 `clash-party-` 和 `mihomo-party-` 开头的两套文件。这是改名过渡期留下的，我们核对过两套文件的 SHA256 校验值，内容完全一样，选哪套都行。
- `.sha256` 结尾的是校验文件，`latest.yml` 是软件自动更新用的，这些都不是安装包。
- 版本号会随更新变化，只看系统和架构的标记就行。

## 安装

### Windows

- 安装版：双击 `setup.exe`，按提示完成安装。
- 便携版：用 7-Zip 之类的解压软件把 `.7z` 解压到一个固定的文件夹，运行里面的 Clash Party 即可。
- 也可以用 WinGet 安装：

```
winget install Mihomo-Party.Clash-Party
```

### macOS

1. 按芯片类型下载 `.pkg` 文件（在“关于本机”里可以看到是 Apple M 芯片还是 Intel）。
2. 双击 `.pkg`，按安装器提示完成安装，过程中需要输入电脑密码。
3. 也可以用 Homebrew 安装：

```
brew install --cask clash-party
```

官方文档里有些地方还写着 dmg 安装包和旧的 `mihomo-party` 命令，以上面最新的方式为准。

### Linux

```
# Debian / Ubuntu
sudo apt install -y ./clash-party-linux-2.0.4-amd64.deb

# Fedora 等
sudo dnf install ./clash-party-linux-2.0.4-x86_64.rpm
```

把文件名换成你实际下载的那个即可。

### 首次打开

第一次打开时，软件会显示“欢迎使用 Clash Party”的交互式教程，会依次介绍导航栏、订阅管理、系统代理和虚拟网卡。熟悉的话可以点右上角直接关掉，之后也能在设置里重新打开。

## 导入订阅

Clash Party 本身不提供节点，需要导入你的订阅链接才能使用。

1. 在订阅服务的用户中心复制 Clash 订阅链接。
2. 点击左侧导航栏的“订阅管理”卡片。
3. 在顶部的“请输入您的订阅网址”输入框里粘贴链接，点击“导入”。
4. 看到“订阅导入成功”的提示就好了。导入多个订阅时，点击要用的那张订阅卡片就能切换。

如果服务商后台有“一键导入 Clash”按钮，在已经安装 Clash Party 的电脑上点它，也可以直接导入。Clash Party 使用的是 `mihomo://install-config?url=` 格式的导入链接。

订阅卡片上会显示流量使用进度和剩余天数，方便随时查看套餐还剩多少。

还没有 Clash 订阅的话，可以参考这份 [Clash 节点购买推荐](https://tuijianvpn.com/4191)，先选一家支持 Clash 订阅的服务，建议从月付开始试用。

## 选择节点与出站模式

点击导航栏的“代理组”卡片，进入“代理组与节点”页面。

- 点代理组旁边的“测试”做一次延迟测试，再点一个延迟正常的节点。
- 节点名称里常见 `0.5x`、`2x` 这样的标记，代表节点倍率，也就是用这个节点时套餐流量的扣除倍数。具体怎么算可以看这篇 [节点倍率是什么意思](https://tuijianvpn.com/9231)。

导航栏的“出站模式”卡片可以切换三种模式：

| 模式 | 流量怎么走 | 适合场景 |
|--|--|--|
| 规则 | 按订阅里的规则自动分流，国内网站直连，国外网站走节点 | 日常使用，推荐默认 |
| 全局 | 所有流量都走你选中的节点 | 临时排查某个网站是否被规则误判 |
| 直连 | 所有流量都不走代理 | 临时关掉代理但不想退出软件 |

## 开启代理：系统代理还是虚拟网卡

导入订阅后，内核就已经在运行了。不过要让浏览器等应用自动走代理，还需要在导航栏打开下面其中一个开关：

| 对比项 | 系统代理 | 虚拟网卡 |
|--|--|--|
| 原理 | 修改系统的代理设置，应用自己决定是否遵守 | 即常说的 TUN 模式，内核接管系统流量 |
| 覆盖范围 | 浏览器和大多数遵守系统代理的软件 | 包括不遵守系统代理的软件，比如游戏、命令行 |
| 使用门槛 | 打开开关即可 | 需要管理员权限，按提示授权 |

简单来说：只是浏览网页，开“系统代理”就够了；遇到某些软件不走代理，再开“虚拟网卡”。

在 Windows 上第一次开虚拟网卡时，软件会提示“启用 TUN 模式需要管理员权限，是否现在重启应用获取权限？”，确认后在弹出的系统对话框里点“是”就行。

## 怎么确认已经连上

- 导航栏的“系统代理”或“虚拟网卡”开关显示已打开。
- “代理组与节点”页面里，当前节点有正常的延迟数值，而不是超时。
- 用浏览器打开一个国外网站，能正常加载。

## 常见问题

### 开机后电脑没网

官方给出的原因是：开着系统代理，却没有打开开机自启。电脑重启后系统代理设置还在，但 Clash Party 没有运行，所以上不了网。在设置里打开“开机自启”就能解决；也可以把系统代理的“代理模式”改成 PAC。

### 订阅导入失败

- 检查链接是否复制完整，有没有多出空格或换行。
- 如果订阅地址本身需要代理才能访问，导入时勾选输入框旁边的“代理”。
- 在订阅服务的用户中心重置一次订阅链接，再重新导入。

### 虚拟网卡打不开

先在“虚拟网卡”页面点“手动授权内核”。Windows 上还可以试试同一页面的“重设防火墙”。如果还是不行，先用系统代理。

### Linux 提示“加密不可用”

官方的解决办法是：在虚拟网卡设置里点“手动授权内核”，输入系统密码，然后点确定。

### macOS 安装失败

官方文档的 macOS 常见问题页提供了一组清理命令，用来卸载旧的后台服务和残留文件，清理并重启电脑后再重新安装。详见 [官方 macOS 故障排除](https://clashparty.org/docs/issues/macos)。

### 和 Clash Verge Rev 有什么区别

两者都基于 Mihomo 内核，都支持 Windows、macOS 和 Linux，订阅链接可以通用。Clash Party 的界面是卡片式导航栏，还内置了 Smart 内核和 Sub-Store 订阅管理，并且仍然提供 Windows 7 和 macOS 10.15 的安装包；Clash Verge Rev 用的人更多（GitHub 星标约 15.7 万，Clash Party 约 2.7 万），遇到问题更容易搜到答案。两个都可以试试，看哪个用着顺手。Clash Verge Rev 的用法见 [Clash Verge Rev 下载与使用教程](https://volya2026.github.io/proxy-client-guide/clash-verge-rev/)。

### Smart 内核是什么

Smart 内核是 Clash Party 内置的另一种内核，可以根据网络情况自动挑选节点。新手不用管它，保持默认就能正常使用。

## 相关链接

- [Clash Party 官方仓库](https://github.com/mihomo-party-org/clash-party)
- [Clash Party 官方文档](https://clashparty.org/docs/handson)
- [代理客户端下载与配置教程索引](https://volya2026.github.io/proxy-client-guide/)

---

由 [推荐VPN](https://tuijianvpn.com/) 整理。本页与 Clash Party 官方无关，如有错误欢迎提 Issue 指出。

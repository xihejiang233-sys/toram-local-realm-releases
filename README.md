# 托拉姆物语本地世界 · Windows 单机包

**r4（纯 C# 单文件整合包 · Win64）** 让 Steam 版《托拉姆物语》进入由本机服务端运行的单人地图，角色进度保存在本机。服务端为 .NET 8 自包含单文件 EXE，支持 Windows 10/11 x64，无需另装 .NET、PowerShell 7 或 Python。使用 Steam 客户端前请先安装游戏和 Clash Verge。

[下载 r4 ZIP](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/download/r4/ToramLocalRealm-CSharp-Win64-AllInOne.zip) · [GitHub Release](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/tag/r4) · [羽毛杯下载页](https://feathercup.pages.dev/downloads) · [r3 历史版本](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/tag/r3) · [r2 历史版本（PowerShell）](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/tag/r2)

## 三步快速上手

先把 ZIP 完整解压到可写目录。启用 Clash Verge 的 Rule（规则）模式，并让 TUN 接收游戏 UDP。

1. 双击 `2-启动本地服(自动接入Clash路由与中继).cmd`，等待服务就绪，再从 Steam 启动游戏并照常登录。启动器将指定世界端点的 UDP 流量接入本机 `38180` SOCKS5 UDP 中继。登录和认证继续沿用原代理规则，挂载与恢复时核对并保留 Selector 选中项。
2. 双击 `3-打开GM控制台与中文物品速查.cmd`，浏览器会打开 `http://127.0.0.1:38181/`。内置 7,059 条物品索引，支持按 ID 或繁简中文名称查询物品与锻晶。需要管理权限的操作使用启动窗口显示的本机 GM 令牌。
3. 退出游戏后双击 `4-恢复官服路由并停止服务.cmd`。路由恢复后，可再次从 Steam 打开官服。

## 存档迁移与世界端点

先停服并备份 r2。在 r4 第一次启动前，将旧包的 `profiles/*.json` 复制到新包的 `profiles/`，包含已有的 `active-profile.json`。保留旧包以便回退。

内置 `tgs01` 至 `tgs40` 范围内的 37 个已配置世界服。`defaults/profiles/` 提供三个可选试跑档，分别为 `phalanx-smoke.json`、`kuzto-boss-smoke.json`、`forest-wolf-smoke.json`。现有 `.avatars.json` 分离式衣柜存档可继续使用。

## r4 更新

- 修复流水线普攻的命中结算顺序（`act=40` 先于 `act=7`），恢复每次有效命中的 +39 AMPR、普通怪 `Event 7` 掉落结算及尸体溶解、消失和刷怪位释放流程。
- 定点 Boss 入场先发 `Event 27`，再回 `Opcode 12`。库斯特（Kuzto / 庫斯特，`24100:U587`，拉比蘭斯地區・廣場）在 HP ≤80% 和 ≤50% 时经 `Event 20` 切换形态。实现覆盖 64 个 Boss 的 170/170 个可破坏部位和 `PartAttack(9)`。胜利结算使用 `Dictionary<byte,object>` 的 `Event 7 / action 212`，聊天栏记录通关用时，`Opcode 94` 胜利退出后自动回广场。
- 恢复 RC3 的 Quick Loader、Cross Fire、Chronos Shift，以及 r2 的宠物融合与技能成长。恢复 `.avatars.json` 分离式衣柜存档兼容，内置 37 个世界服和 3 个可选试跑档。

## Steam 实机记录

Steam 零售客户端 `v2.2.8s` 第 12、13 轮实测 Easy 庫斯特从 350,000 HP 自然击杀至 0，服务端记录胜利退出，第 13 轮看到 `00:02:56` 通关记录并自动回到广场。第 12 轮普通怪实测 7 次命中各回复 39 MP，拾取掉落，并在约 14 秒的同镜头采样看到首只怪物模型消失，随后可移动和继续战斗。排名和奖励界面仍待验证。

## 文件校验

ZIP 共 23 个文件，大小为 **44,130,074 字节（42.09 MB）**。SHA-256 为 `ae668735bf4b5f02a9fe92cead1a04eab06b08034b1d8e1d6064ee57e52383dd`。

```powershell
Get-FileHash -Algorithm SHA256 .\ToramLocalRealm-CSharp-Win64-AllInOne.zip
```

[SHA-256 校验文件](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/download/r4/ToramLocalRealm-CSharp-Win64-AllInOne.zip.sha256) · [包内文件清单](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/download/r4/PACKAGE-MANIFEST.json)

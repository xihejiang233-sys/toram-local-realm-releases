# 托拉姆物语本地世界 · Windows 单机包

**r3（纯 C# 单文件整合包 · Win64）** 让 Steam 版《托拉姆物语》进入由本机服务端运行的单人地图，角色进度保存在本机。服务端为 .NET 8 自包含单文件 EXE，支持 Windows 10/11 x64，无需另装 .NET、PowerShell 7 或 Python。使用 Steam 客户端前请先安装游戏和 Clash Verge。

[下载 r3 ZIP](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/download/r3/ToramLocalRealm-CSharp-Win64-AllInOne.zip) · [GitHub Release](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/tag/r3) · [羽毛杯下载页](https://feathercup.pages.dev/downloads) · [r2 历史版本（PowerShell）](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/tag/r2)

## 三步快速上手

先把 ZIP 完整解压到可写目录。启用 Clash Verge 的 Rule（规则）模式，并让 TUN 接收游戏 UDP。

1. 双击 `2-启动本地服(自动接入Clash路由与中继).cmd`，等待服务就绪，再从 Steam 启动游戏并照常登录。启动器将指定世界端点的 UDP 流量接入本机 `38180` SOCKS5 UDP 中继。登录和认证继续沿用原代理规则，挂载与恢复时核对并保留 Selector 选中项。
2. 双击 `3-打开GM控制台与中文物品速查.cmd`，浏览器会打开 `http://127.0.0.1:38181/`。内置 7,059 条物品索引，支持按 ID 或繁简中文名称查询物品与锻晶。需要管理权限的操作使用启动窗口显示的本机 GM 令牌。
3. 退出游戏后双击 `4-恢复官服路由并停止服务.cmd`。路由恢复后，可再次从 Steam 打开官服。

## 存档迁移与世界端点

先停服并备份 r2。在 r3 第一次启动前，将旧包的 `profiles/*.json` 复制到新包的 `profiles/`，包含已有的 `active-profile.json`。保留旧包以便回退。

默认世界域名为 `tgs02/21/30/31.toram.jp`。如果实际分配到其他已确认的世界服，例如 `tgs37.toram.jp`，在 `config/realm-settings.json` 中把 `additionalWorldEndpoints` 设为 `["tgs37.toram.jp"]`，保存后重启本地服。

## Steam 实机记录

Round 7 使用 Steam `v2.2.8s`。两次登录均为 0 次重连，单次普攻击中结算实测 4.7831 ms（< 5 ms），连续 12 次普攻各回复 39 MP（+39 AMPR）。跨图、冷重启读档和 Clash 路由恢复已验证。GM 发放的道具在跨图和重登后可从客户端背包看到，Lv174 Boss 的客户端显示和 Orb Shop 余额显示仍待验证。

## 文件校验

ZIP 共 21 个文件，大小为 **44,094,670 字节**。SHA-256 为 `c5cd523d0a0735511fd279528053e042a9234582ae9dde69e1f28d45337b5c5d`。

```powershell
Get-FileHash -Algorithm SHA256 .\ToramLocalRealm-CSharp-Win64-AllInOne.zip
```

[SHA-256 校验文件](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/download/r3/ToramLocalRealm-CSharp-Win64-AllInOne.zip.sha256) · [包内文件清单](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/download/r3/PACKAGE-MANIFEST.json)

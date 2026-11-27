# 托拉姆物语本地世界 · Windows 单机包

Toram Local Realm 让 Steam 版《托拉姆物语》在本机运行单人地图，角色进度保存在本机。支持 Windows 10/11，使用系统自带的 Windows PowerShell 5.1，无需另装运行依赖。请先安装 Steam 版游戏。

[下载 r1 ZIP](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/download/r1/ToramLocalRealm-Windows-LocalPlay-AllInOne-r1.zip) · [GitHub Release](https://github.com/xihejiang233-sys/toram-local-realm-releases/releases/tag/r1) · [羽毛杯备用下载页](https://feathercup.pages.dev/downloads)

## 三步快速上手

1. 下载 ZIP，完整解压到可写目录。
2. 双击 `Play-LocalRealm.cmd`，选 **[1] 自动启动**。如有 UAC 提示，确认后继续。如 Clash Verge 提示应用临时规则，输入 `y`。等待出现 `REALM_READY`。
3. 从 Steam 打开《托拉姆物语》，照常登录并进入地图。登录连接官方服务器，地图和本地存档由本机服务端处理。

## 三种连接模式

| 网络环境 | 启动方式 |
| --- | --- |
| 系统 hosts | 普通网络选 **[1] 自动启动**。启动器临时将地图域名指向本机。 |
| Clash Verge TUN | 保持 TUN 开启并选 **[1] 自动启动**。启动器通过临时规则把地图连接送到本机 SOCKS5 UDP 中继，登录沿用现有代理规则。 |
| 手动代理 | FlClash 等客户端选 **[3]**，也可运行 `Start-ServerWithRelayOnly.cmd`。看到 `RELAY_ONLY_READY` 后，按包内 `README.zh-CN.md` 将 `config/clash-manual-snippet.yaml` 中的地图规则合并到代理配置，核对中继端口并启用 SOCKS5 UDP 转发。 |

## 停服并切回官服

先退出游戏，在启动器选 **[2]**，或双击 `Stop-LocalServer.cmd`。自动启动模式会恢复官服路由。若只需恢复自动路由，可运行 `Restore-OfficialRoute.cmd`。手动代理模式需在代理客户端禁用或移除本次添加的规则。完成后从 Steam 重新打开游戏。

## 三套内置存档

停服后在菜单选 **[4]**。选中存档后按 `S` 切换，按 `R` 并确认则重置所选存档。

| 存档 | 初始状态 |
| --- | --- |
| `starter` | Lv1 法杖角色，从洛库库平原开始，首次启动默认选中。 |
| `explorer-lv27` | Lv27 单手剑角色，从迈巴罗森林开始，可探索森林狼入口。 |
| `demo-lv160` | Lv160 演示角色，从洛库库平原开始，可体验高级装备和技能。 |

## SHA-256 校验

ZIP 大小为 **2,739,341 字节**，内含 283 个文件。SHA-256 为 `c9e846179faa753166c9df38fa347d95b38f0b1025a231480a08bf4911e885b6`。

在下载目录运行以下命令，核对输出的 Hash。

```powershell
Get-FileHash -Algorithm SHA256 .\ToramLocalRealm-Windows-LocalPlay-AllInOne-r1.zip
```

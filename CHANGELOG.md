# OpenWrt MT6000 配置文件详单

> 更新时间：2026-04-28
> OpenWrt 版本：v25.12.2
> 目标设备：GL.iNet GL-MT6000 (mediatek/filogic)

---

## 1. 目标平台

| 配置项 | 值 |
|--------|-----|
| `CONFIG_TARGET_mediatek` | y |
| `CONFIG_TARGET_mediatek_filogic` | y |
| `CONFIG_TARGET_mediatek_filogic_DEVICE_glinet_gl-mt6000` | y |
| `CONFIG_CPU_TYPE` | cortex-a53 |
| `CONFIG_ARCH_64BIT` | y |
| `CONFIG_LINUX_6_12` | y |

---

## 2. 文件系统

| 配置项 | 值 |
|--------|-----|
| `CONFIG_TARGET_ROOTFS_SQUASHFS` | y |
| `CONFIG_TARGET_SQUASHFS_BLOCK_SIZE` | 256 |
| `CONFIG_TARGET_INITRAMFS_COMPRESSION_XZ` | y |

---

## 3. 基础软件包

### 3.1 网络相关

| 软件包 | 说明 |
|--------|------|
| `firewall4` | 防火墙 (nftables) |
| `dnsmasq-full` | DNS/DHCP 服务器 |
| `netifd` | 网络接口管理 |
| `odhcp6c` | IPv6 DHCP 客户端 |
| `odhcpd-ipv6only` | IPv6 DHCP 服务器 |
| `wpad-basic-mbedtls` | WPA supplicant |

### 3.2 系统工具

| 软件包 | 说明 |
|--------|------|
| `dropbear` | SSH 服务器 |
| `uhttpd` | Web 服务器 |
| `opkg` | 包管理器 |
| `procd` | 进程管理 |
| `ubus` | RPC 总线 |

---

## 4. LuCI Web 界面

### 4.1 核心组件

| 软件包 | 说明 |
|--------|------|
| `luci-base` | LuCI 基础库 |
| `luci-mod-admin-full` | 完整管理界面 |
| `luci-mod-dashboard` | 仪表盘 |
| `luci-mod-network` | 网络配置 |
| `luci-mod-status` | 状态页面 |
| `luci-mod-system` | 系统设置 |

### 4.2 LuCI 主题

| 软件包 | 说明 |
|--------|------|
| `luci-theme-bootstrap` | Bootstrap 主题 |

### 4.3 LuCI 应用

| 软件包 | 说明 |
|--------|------|
| `luci-app-dockerman` | Docker 管理 |
| `luci-app-firewall` | 防火墙配置 |
| `luci-app-mwan3` | 多线负载均衡 |
| `luci-app-package-manager` | 包管理器界面 |
| `luci-app-passwall` | 代理工具 |
| `luci-app-samba4` | Samba 文件共享 |
| `luci-app-uhttpd` | Web 服务器配置 |
| `luci-app-wol` | 网络唤醒 |

### 4.4 LuCI 国际化 (中文)

| 软件包 | 说明 |
|--------|------|
| `luci-i18n-base-zh-cn` | 基础翻译 |
| `luci-i18n-dashboard-zh-cn` | 仪表盘翻译 |
| `luci-i18n-dockerman-zh-cn` | Docker 管理翻译 |
| `luci-i18n-firewall-zh-cn` | 防火墙翻译 |
| `luci-i18n-mwan3-zh-cn` | MWAN3 翻译 |
| `luci-i18n-package-manager-zh-cn` | 包管理器翻译 |
| `luci-i18n-passwall-zh-cn` | Passwall 翻译 |
| `luci-i18n-samba4-zh-cn` | Samba 翻译 |
| `luci-i18n-uhttpd-zh-cn` | Web 服务器翻译 |
| `luci-i18n-wol-zh-cn` | 网络唤醒翻译 |

---

## 5. Passwall 配置

| 配置项 | 说明 |
|--------|------|
| `CONFIG_PACKAGE_luci-app-passwall` | Passwall 主程序 |
| `CONFIG_PACKAGE_luci-app-passwall_Nftables_Transparent_Proxy` | NFTables 透明代理 |
| `CONFIG_PACKAGE_luci-app-passwall_INCLUDE_Geoview` | 包含 GeoIP 规则 |
| `CONFIG_PACKAGE_luci-app-passwall_INCLUDE_Haproxy` | 包含 HAProxy |
| `CONFIG_PACKAGE_luci-app-passwall_INCLUDE_SingBox` | 包含 SingBox |
| `CONFIG_FEED_passwall_luci` | Passwall 源 |

---

## 6. 固件相关

| 软件包 | 说明 |
|--------|------|
| `u-boot-mt7986_glinet_gl-mt6000` | U-Boot 引导程序 |
| `mt7986-wo-firmware` | 无线固件 |
| `trusted-firmware-a-mt7986-*` | ARM 固件 |
| `kmod-mt7915e` | MT7915 WiFi 驱动 |
| `kmod-mt7986-firmware` | MT7986 固件 |

---

## 7. 已删除/未启用的包

以下包因依赖问题已删除：

- `luci-app-mjpg-streamer` (缺少 mjpg-streamer)
- `luci-app-mtwifi` (缺少 kmod-mt_wifi)
- `luci-app-nginx-pingos` (缺少 libpcre)
- `luci-app-nps` (缺少 npc)
- `luci-app-webd` (缺少 webd)
- `onionshare-cli` (缺少 python3-pysocks/python3-unidecode)
- `rblibtorrent`, `trojan`, `trojan-plus` (缺少 boost-system)
- `luci-app-homeproxy`, `sing-box-tiny` (递归依赖)
- `luci-app-kodexplorer` (递归依赖)
- `luci-app-qbittorrent`, `qbittorrent` (递归依赖)
- `luci-app-alist` (递归依赖)

---

## 8. Feeds 源

| 源名称 | 地址 |
|--------|------|
| `passwall_packages` | Openwrt-Passwall/openwrt-passwall-packages.git;main |
| `passwall_luci` | Openwrt-Passwall/openwrt-passwall.git;main |
| `smpackage` | kenzok8/small-package.git |
| `daixiao` | NoviceDai/OpenwrtAddon.git |

# 小米路由器 OpenWrt + Clash 配置

将小米路由器刷入 OpenWrt，实现家庭网络全局科学上网。

## 适用路由器

| 型号 | Flash | RAM | 推荐度 |
|------|-------|-----|--------|
| 小米 AX3600 | 256MB | 512MB | 5星 |
| 小米 AX1800 | 128MB | 256MB | 3星 |
| 红米 AX5 | 128MB | 256MB | 3星 |

## 刷机准备

### 1. 解锁 SSH

小米路由器需要先解锁 SSH：

```bash
# 使用 MIWIFI 开放平台
# 登录路由器官网绑定设备
# 获取 SSH 权限
```

### 2. 刷入 OpenWrt

```bash
ssh root@192.168.31.1
cd /tmp
wget https://downloads.openwrt.org/snapshots/targets/mediatek/filogic/openwrt-xxx.bin
sysupgrade -F openwrt-xxx.bin
```

## OpenWrt 基础配置

```bash
# 设置密码
passwd

# 安装必要包
opkg update
opkg install luci-app-clash
opkg install ca-bundle
```

## Clash 配置

通过 LuCI（Web 界面）：访问 `192.168.1.1` > 服务 > Clash，填入订阅链接或手动配置，启用 TUN 模式。

## 常见问题

**路由器发热？** OpenWrt 长期运行温度较高，建议加装散热片。

**Flash 不够？** 使用 USB 存储扩展，安装 Clash 到 U 盘。

---

推荐工具：

- [Clash for Windows](https://clashforwindows.site/)
- [ClashMI](https://clashmi.site/)
- [FlClash](https://flclash.us/)

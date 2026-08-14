# NOTICE

This repository is a **fork** of [gokele/ovh](https://github.com/gokele/ovh), maintained by **liuweiqiang0523**.

本仓库是 [gokele/ovh](https://github.com/gokele/ovh) 的 **fork**，由 **liuweiqiang0523** 维护。

## Upstream (上游)

- Project: OVH Console — real-time OVH dedicated server / VPS stock monitor with auto-ordering, multi-account management, and Telegram notifications.
- Project: OVH 控制台 — 实时 OVH 独服/VPS 库存监控，支持自动下单、多账户管理、Telegram 通知。
- Source: https://github.com/gokele/ovh
- License: see `LICENSE` (kept from upstream / 保留上游许可).
- Original author: gokele.

## Fork scope (本 fork 范围)

Local maintenance patches only — full upstream functionality is preserved.
仅包含本地维护补丁，上游全部功能保持不变。

See `MAINTAINING.md` for the patch list.
补丁清单见 `MAINTAINING.md`。

## Production deployment (生产部署)

This fork's production deployment runs on the owner's OVH host as a systemd service
(`ovh-gokele.service`, binary at `/opt/ovh-gokele/bin/ovh-server`), with data in
`/opt/ovh-gokele/data/sniper.db` (SQLite). Production config is **never** committed to this repo.
本 fork 的生产部署运行在维护者的 OVH 主机上，作为 systemd 服务
（`ovh-gokele.service`，二进制位于 `/opt/ovh-gokele/bin/ovh-server`），数据存放于
`/opt/ovh-gokele/data/sniper.db`（SQLite）。生产配置**绝不**提交到本仓库。

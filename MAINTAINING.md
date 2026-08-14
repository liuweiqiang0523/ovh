# Maintainer Notes (维护说明)

This fork adds a **local maintenance patch** on top of upstream `gokele/ovh v0.0.8`.
本 fork 在上游 `gokele/ovh v0.0.8` 之上维护一个本地补丁。

## Patch list (补丁清单)

| # | File | Purpose (用途) |
|---|------|----------------|
| 1 | `server/internal/monitor/loop.go` | **fix: transient Telegram network errors no longer permanently stop the monitor loop** — only a genuinely invalid config (missing token / invalid token / invalid chat) stops monitoring; a single timeout/connect failure now logs a warning and keeps polling. Fixes 7 days of silent monitoring outage caused by one `getMe` timeout. / **修复：瞬时 Telegram 网络错误不再永久停止监控循环** — 仅配置真正失效（未配置 / Token 无效 / ChatID 无效）才停机；单次超时/连接失败只记警告并继续轮询。修复因一次 `getMe` 超时导致监控静默停止 7 天的问题。 |

## Applying patches after upstream sync (上游同步后重新打补丁)

```bash
# after merging upstream changes, re-apply patch #1 by hand:
# 合并上游改动后，手动重新应用 #1 补丁：
#   server/internal/monitor/loop.go — checkTGOrStop():
#     - if strings.Contains(reason, "无法连接") -> Warn + continue
#     - else -> Error + Stop()
```

## Build (编译)

Requires Go 1.25+. The production binary is built with the UI embedded:
需要 Go 1.25+。生产二进制需内嵌前端 UI 编译：

```bash
cd server
go build -tags ui -trimpath -ldflags "-s -w" -o ovh-server .
```

## Verify (验证)

```bash
# 1. build passes 编译通过
cd server && go vet -tags ui ./internal/monitor/ && go build -tags ui ./...
# 2. runtime: monitor loop must log "监控循环已启动" and keep checking subscriptions
#    运行时：监控循环应输出 "监控循环已启动" 并持续检查订阅
systemctl status ovh-gokele.service   # on the production host / 生产机上
```

## Rollback (回滚)

Production binary backups on the OVH host:
生产机二进制备份：

- `bin/ovh-server.pre-fix-20260814-153606` — pre-fix binary / 修复前
- `bin/ovh-server.official-v0.0.8.20260729-115037` — original official v0.0.8 / 官方原版

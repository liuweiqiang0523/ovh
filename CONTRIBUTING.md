# Contributing / 贡献指南

This fork is a personal maintenance fork of [gokele/ovh](https://github.com/gokele/ovh).
本仓库是 [gokele/ovh](https://github.com/gokele/ovh) 的个人维护 fork。

## Rules / 规则

1. Upstream-first: feature requests and upstream-worthy fixes should go to the **upstream project** first. This fork only carries local patches needed for the maintainer's own production deployment.
   上游优先：功能请求和值得上游修复的问题应首先提交给**上游项目**。本 fork 仅承载维护者自身生产部署所需的本地补丁。
2. Every local patch must be documented in `MAINTAINING.md`.
   每个本地补丁必须在 `MAINTAINING.md` 中记录。
3. Production config, credentials, and runtime data are never committed.
   生产配置、凭据和运行数据一律不提交。

## Patch workflow / 补丁流程

1. Branch from `main`.
2. Apply the change and add/update the corresponding entry in `MAINTAINING.md`.
3. Verify: `cd server && go build -tags ui ./...` (Go 1.25+).
4. Open a PR against this fork's `main`.

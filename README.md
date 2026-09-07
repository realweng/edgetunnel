# edgetunnel 私有部署

基于 [cmliu/edgetunnel](https://github.com/cmliu/edgetunnel) 的私有 fork，仅用于自动升级流水线，不含文档与截图。

## 自动升级流水线

- `sync.yml`（上游自带）：每天 UTC 00:00 同步上游 main 分支
- `deploy.yml`：每天 UTC 02:45 检测 `_worker.js` 变化后自动部署到 Cloudflare Pages；`workflow_dispatch` 可手动触发；wrangler@latest 失败自动回退到固定版本
- `keepalive.yml`：每周一检查仓库活跃度，防止 GitHub 暂停定时任务（60 天无提交规则）

## 敏感信息位置

- 订阅 token、UUID、PROXYIP 等运行配置：Cloudflare KV（不在本仓库）
- `CF_API_TOKEN` / `CF_ACCOUNT_ID`：仓库 Actions Secrets（加密）
- 本仓库不含任何截图、订阅链接或节点信息

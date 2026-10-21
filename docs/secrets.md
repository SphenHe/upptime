# Repository Secrets

当前原则：服务器地址（IP 或主机名）和端口继续保存在 Repository Secrets；Qwen 校外入口使用 Secret；其余 Web 服务地址直接写入 `.upptimerc.yml`。认证凭据继续使用 Secrets。

## 当前监测引用（11 个）

| Secret | 用途 |
| --- | --- |
| `QWEN_HEALTH_URL` | Qwen 校外入口的完整 /health 地址 |
| `AZURE_VPS_URL` / `AZURE_VPS_SSH_PORT` | 原 Azure-VPS 在线检查 |
| `TSINGHUA_VPS_URL` / `TSINGHUA_VPS_SSH_PORT` | 原 Tsinghua-VPS 在线检查 |
| `COMPAQ_HOST` / `COMPAQ_SSH_PORT` | compaq SSH 检查；主机地址同时用于 RustDesk |
| `ALIYUN_HOST` / `ALIYUN_SSH_PORT` | aliyun SSH 检查 |
| `RUSTDESK_ID_PORT` / `RUSTDESK_RELAY_PORT` | RustDesk 两个 TCP 检查的端口 |

`GH_PAT` 是 GitHub 自动化认证凭据，由工作流单独传入，不包含在上述 11 个上下文 Secret 中。监测不需要 SSH 私钥、SSH 口令或生产推理 API Key。

## 明文 Web 地址

HedgeDoc、Pastebin、Vaultwarden、Blog、MonkeyFile、TsinghuaMemes 沿用原有明文 URL。IT Tools、Grafana 校外入口、API Proxy 校外入口现已改成明文 URL。Qwen 实际入口不写入仓库。

## 工作流和既有 Secrets

`.upptimerc.yml` 的精确白名单与 `uptime.yml`、`response-time.yml`、`setup.yml` 的 SECRETS_CONTEXT 一致。当前未用到的 Secrets 暂留 GitHub，但不再注入这些检查工作流；原有 Secret 值未被覆盖或删除。

原 Azure/Tsinghua Secret 不能通过 GitHub API 回读，本次保留原引用，不猜测或更换目标。不需要用户提供这些值。

配置及工作流由 Git 管理；线上执行结果以 GitHub Actions 为准。

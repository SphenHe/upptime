# 按服务器整理的服务与观测范围

检查时间：2026-10-21 14:17（Asia/Singapore）。部署清单依据 SSH、Docker 和 systemd 只读检查；“容器/进程运行”不能代替业务可用性验证。已从 Upptime 取消观测的应用不会因此停止运行。

| 服务器 | 已发现的部署服务 | 当前纳入 Upptime 的服务观测 |
| --- | --- | --- |
| Azure | 主域名 Caddy 入口：域名解析与 Azure 别名一致，欢迎页可访问；主机密钥未核实，未登录盘点其他服务 | 仅服务器在线，取消 Caddy |
| compaq | HedgeDoc、IT Tools、Vaultwarden、RustDesk、Wakapi、MTranServer、Mihomo；Ghosthunter 已排除观测 | HedgeDoc、IT Tools、Vaultwarden、RustDesk ID / Relay，共 5 项 |
| aliyun | OpenAgents API / Worker、Nginx、Cloudflare Tunnel | 无独立业务观测 |
| h100 | CLIProxyAPI、CPA Manager、Mihomo、入口 Caddy；Grafana、VictoriaMetrics、vmagent；OpenLDAP；Cloudreve；DeTikZify；3 个 GitLab Runner；MySQL、Redis、Tailscale；Nextcloud 仍部署但已取消观测 | API Proxy、Grafana 各一个校外隧道入口，共 2 项 |
| h200 | vmagent、node-exporter、DCGM exporter、Tailscale | 无独立业务观测 |
| a6000 | 智能助手前端、后端、PostgreSQL/pgvector、Redis；Caddy；主机/GPU 监控。后端容器仍反复重启 | 全部取消观测 |
| pro6000 | 智能助手前端、后端、数据库、Redis；主机/GPU 监控；VMware 来宾进程正在运行。Qwen3.8-27B-FP8 已按请求部署到 GPU 1；ESAS 为既有 Windows 来宾部署记录 | 仅 Qwen 校外隧道入口；不检查服务器在线，推理限定 GPU 1 |
| liuguodong | vmagent、node-exporter | 全部取消观测 |
| zhaoxingyu | vmagent、node-exporter | 全部取消观测 |
| heying | vmagent、node-exporter | 全部取消观测 |
| cat | UOJ、Open WebUI/Pipelines、Cloudreve、Portainer、CFile/GHFile/MPCFile、Leaderboard、AE9AP9、NIA agent、Geant4 开发容器、2 个 GitLab Runner、主机监控；Overleaf 与 MongoDB 反复重启 | 全部取消观测 |
| kaiser | UOJ、HedgeDoc、Seafile、Gitea、Leaderboard、StudentRight、CFile/GHFile、主机/GPU 监控 | 全部取消观测 |
| 原 Tsinghua-VPS 条目 | 目标保存在既有 Secret 中，尚未确认与哪一个服务器别名对应，不能据名称合并 | 沿用既有 TCP 检查 |

另有 Pastebin/PasteShare、Blog、MonkeyFile、TsinghuaMemes 4 项网站观测，当前尚未核实对应宿主机，因此单独保留，不随意归属到上述服务器。

## 当前观测范围

当前只保留 Azure-VPS、原 Tsinghua-VPS、COMPAQ、ALIYUN 共 4 项服务器在线观测。

Azure 不观测 Caddy；h100、h200、cat、kaiser、a6000、pro6000、liuguodong、zhaoxingyu、heying 的服务器在线检查均取消。pro6000 只保留 Qwen 校外隧道入口，推理限定 GPU 1。h100 不观测 Cloudreve 和 Nextcloud。

此前的部署盘点仅记录应用实际存在情况，不能据此判断应用已纳入观测。以 [当前观测列表](service-inventory.md) 为准。当前共 16 项观测，线上执行结果以 GitHub Actions 为准。

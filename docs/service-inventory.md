# 观测列表

当前保留 **16 项**：12 项网站/服务观测、4 项服务器在线观测。

## Service（9 项）

| 观测项 | 检查内容 |
| --- | --- |
| HedgeDoc（compaq） | HTTP 页面 |
| Pastebin / PasteShare | HTTP 页面 |
| Vaultwarden（compaq） | HTTP 页面 |
| IT Tools（compaq） | HTTP 页面 |
| Grafana（隧道） | HTTP /api/health 和数据库状态 |
| API Proxy（隧道） | HTTP 页面 |
| Qwen 入口（隧道） | 推理引擎 /health 经网关检查 |
| RustDesk ID（compaq） | TCP 连通性 |
| RustDesk Relay（compaq） | TCP 连通性 |

## Pages（3 项）

| 观测项 | 检查内容 |
| --- | --- |
| Blog | HTTP 页面 |
| MonkeyFile | HTTP 页面 |
| TsinghuaMemes | HTTP 页面 |

## Server（4 项）

| 观测项 | 检查内容 |
| --- | --- |
| Azure-VPS | 原有 TCP 连通性检查 |
| Tsinghua-VPS | 原有 TCP 连通性检查 |
| COMPAQ | SSH 协议标识 SSH-2.0- |
| ALIYUN | SSH 协议标识 SSH-2.0- |

## 范围

- Azure 只观测服务器在线，不检查 Caddy 网站。
- 不检查 h100、h200、cat、kaiser、a6000、pro6000、liuguodong、zhaoxingyu、heying 的服务器在线状态。
- pro6000 仅保留 Qwen 校外隧道入口；Qwen 推理限定宿主 GPU 1，GPU 0 不部署推理。
- h100 保留 API Proxy 和 Grafana 各一个校外隧道入口，取消 Cloudreve、Nextcloud 观测。
- 原 Tsinghua-VPS 条目目标仍由既有 Secret 保存，尚未核实其服务器别名，暂不合并或更改。
- Qwen 入口以及服务器地址和端口使用 Secrets；其余 Web 地址明文。当前精确允许 11 个上下文 Secret，GH_PAT 单独传入。原 Azure/Tsinghua Secret 引用保留，不需要提供其值。
- 本次配置由 Git 版本管理；线上执行与发布状态以 GitHub Actions 为准。

## 本轮验证

Qwen 已在物理 GPU 1 上就绪，内部模型查询和实际聊天推理成功；不带密钥返回 401。从本机访问两条公网 /health 均为 200、正文 OK。网关在后端启动期间返回 502，健康状态没有由静态页面代替。GPU 0 仅保留既有桌面/VMware 进程。

当前本地复测：13 项正常、Blog 返回 404；2 项既有 Secret 目标无法回读复测。上述状态来自此前现场验证，移除直连监控后仅过滤结果，未重复网络探测。线上执行结果以 GitHub Actions 为准。

从 pro6000 宿主访问其 Cloudflare 隧道入口返回 403，而从本机访问正常。该来源差异尚未定位；推送后仍需从 GitHub Actions runner 验证校外入口。

Grafana、API Proxy、Qwen 均只观测校外隧道入口；校内直连服务仍可使用，本次仅取消其 Upptime 检查。

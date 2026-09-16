# InsightGrid

运营商政企客户经理的商机工作台：先判断这条标该不该跟，再提醒该提前找谁。

本仓库是 Apache-2.0 开源空壳。规划已定，应用还不能运行。采集实现、真实客户数据和提示词不在这里。

## 要解决的问题

客户经理太忙，公开标讯看不完，历史中标后的续约窗口也容易漏。

普通标讯工具只回答「最近有哪些公告」。InsightGrid 要回答：

1. **这条该不该跟** — 是否属于通信或 DICT
2. **该提前找谁** — 客户、原中标方，还是其他生态（后续版本）

## 版本

| 版本 | 做什么 | 状态 |
| --- | --- | --- |
| v0.1 | 逢标筛选 | 规划中 |
| v0.2 | 续约提醒 | 未开始 |
| v0.3 | 部门内使用 | 未开始 |

v0.1 不做关系图谱、数据看板和商机评分，也不自动登录抓取正文。

## 谁在用

先做个人工具，再做成部门平台。对外只开框架、说明和脱敏示例。

## v0.1 怎么用

1. 维护关注客户
2. 读取来源网站的公开列表
3. 丢掉土建、物资、后勤等无关公告
4. 对其余标给出分类（通信 / DICT / 不确定）和一句理由
5. 打标：忽略、关注，或需找生态；看正文请打开原链接

来源网站的正文和附件常常要登录。v0.1 不代你登录，也不保存账号或 Cookie。

## 技术栈（v0.1）

Vue 3、FastAPI、PostgreSQL、Docker Compose、APScheduler、云端 OpenAI 兼容 API。

不用 Elasticsearch、图数据库、Redis、向量库和 Kubernetes。

开发和测试先在 macOS 上，随后在 Windows 11 上；两台机器都在 Docker Desktop 里运行，不在宿主机直接装数据库或运行时。

## 仓库结构

```
insightgrid/
├── backend/             # 后端服务
├── frontend/            # 前端工作台
├── collectors/          # 公开仓仅说明，实现不公开
├── processors/          # 清洗与解析
├── ai/                  # AI 分析（提示词不公开）
├── scheduler/           # 定时任务
├── database/            # 迁移脚本
├── tests/
├── docs/
├── examples/            # 脱敏示例
├── scripts/
├── .env.example
├── docker-compose.yml
├── LICENSE
└── README.md
```

安装和运行说明将在 v0.1 可运行后补充。请先安装 Docker Desktop，用同一套 `docker compose` 在 Mac 和 Windows 上启动。

## 数据与合规

只使用合法、公开或已获授权的数据，并遵守来源网站规则和本单位安全要求。

本仓库不放真实客户数据、账号、Cookie、Token、私钥，以及内部接口和业务规则。采集不绕过登录墙。

公开数据记录来源和获取时间。跟进记录留在本地，不进 GitHub。

## 许可

[Apache License 2.0](LICENSE)

# xAgent Releases

[English](README.md)

本仓库用于发布 xAgent Server 官方二进制版本，仅包含发布包、校验文件、版本元数据和授权文件，不包含 xAgent 源代码。

当前版本：[xAgent v0.0.16.beta](https://github.com/coffeehc/xagent-releases/releases/tag/v0.0.16.beta)

使用文档：

- [xAgent 使用手册](https://xagent.xiagaogao.com/)
- [开始安装 xAgent](https://xagent.xiagaogao.com/docs/getting-started/install/)
- [xAgent 产品介绍与核心能力](https://xagent.xiagaogao.com/docs/getting-started/what-is-xagent/)
- [插件](https://xagent.xiagaogao.com/docs/user-guide/agent-plugins/)

## 什么是 xAgent

xAgent 是企业统一的 AI 工作平台。服务端部署，快速接入现有系统，权限与成本集中管控、操作全程审计；员工打开网页或手机，即可使用 AI 完成工作。实现企业可管、员工好用。

xAgent 既是员工统一使用 AI 的入口，也是企业统一管理 AI 的基座。它可以理解目标、处理资料、分析数据、生成成果、调用经过授权的工具，并连接企业现有系统继续完成工作。外部系统原有的账号和权限仍然是访问依据，xAgent 不会凭空扩大用户权限。

![xAgent 仪表板](assets/xagent-dashboard-zh.webp)

## xAgent v0.0.16.beta

本测试版重点更新：

- xAgent 内原 Connector 能力整体升级为 AgentPlugin，保留原有接入逻辑和业务协议语义。
- 管理员在“插件管理”中管理 AgentPlugin Connector，用户只在“插件连接”中管理自己的 Channel。
- 公共描述对象升级为 `AgentPluginDescriptor`，schema 为 `xagent.agentplugin/v2`；官方插件统一使用新的程序、服务、配置根键、安装目录和 R2 制品。
- SQLite 与 PostgreSQL 会把已有插件接入、Channel、VChannel 和 Session purpose 迁移到 AgentPlugin 表与命名空间。
- 从 `0.0.16.beta` 起，Linux 升级会探测已经安装的旧组件，保留完整配置和数据目录，启动替代 AgentPlugin 后才注销旧服务。
- 组件迁移失败时恢复原目录、配置、程序和服务；原先没有安装的组件不会被补装。
- 新增 A2A Client，支持远端 Agent 发现、鉴权、任务操作、流式与轮询监控、重启恢复、收件箱、Artifact、Session 回投和用量统计。
- 企业授权可限制 xAgent 最高版本，并新增 AgentPlugin Channel 与 A2A 连接容量。

支持的平台：

- Linux AMD64
- Linux ARM64
- macOS AMD64
- macOS ARM64

完整功能变化和升级说明见[本版更新日志](changelog/v0.0.16.beta.md)。

## 安装

Linux 和 macOS 使用同一个安装命令：

```bash
curl -fsSL https://downloads.xagent.xiagaogao.com/scripts/install.sh | bash
```

安装器会自动识别平台，下载并校验对应发布包，安装或升级 xAgent，并可选择安装支持的 AgentPlugin。长期运行的服务端部署建议使用 Debian Linux 和 systemd。Windows 当前无法提供与 Linux、macOS 同等的受控脚本沙箱边界，因此暂不建议作为部署环境。

升级前请备份 xAgent 配置、数据库、工作区和 AgentPlugin 状态。部署要求和首次系统初始化流程见[开始安装 xAgent](https://xagent.xiagaogao.com/docs/getting-started/install/)。

## 手动下载

发布文件可从 [GitHub Releases](https://github.com/coffeehc/xagent-releases/releases) 下载。`v0.0.16.beta` 提供以下平台包：

```text
xagent-v0.0.16.beta-linux-amd64.tar.gz
xagent-v0.0.16.beta-linux-arm64.tar.gz
xagent-v0.0.16.beta-darwin-amd64.tar.gz
xagent-v0.0.16.beta-darwin-arm64.tar.gz
```

Release 同时提供：

- `SHA256SUMS`：发布包和发布文件的校验值。
- `BINARY_SHA256SUMS`：每个平台包内可执行文件的校验值。
- `release.json`：可供程序读取的版本与授权元数据。
- `LICENSE`、`EULA.md` 和 `THIRD_PARTY_NOTICES.md`。

每个平台包只包含 xAgent 可执行文件、README、版本元数据和授权文件，不包含源代码。

## 校验下载文件

下载校验文件和 Release 附件后，在安装前执行：

```bash
shasum -a 256 -c SHA256SUMS
```

Linux 也可以使用 `sha256sum -c SHA256SUMS`。如果只下载一个平台包，请计算该文件的 SHA256，并与 `SHA256SUMS` 中对应的一行比较。

## 源码与授权

本仓库发布的是二进制产物。在这里提供二进制文件，不代表对应源码已经开源。软件使用范围以每个 Release 中的 `LICENSE`、`EULA.md` 和第三方声明为准。

## 反馈与安全问题

- [提交想法或反馈普通问题](https://xagent.xiagaogao.com/docs/cooperation/idea/)
- 如果安全问题包含敏感信息，请使用文档提供的私密联系方式，不要通过公开 GitHub Issue 提交。

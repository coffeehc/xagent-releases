# xAgent Releases

[English](README.md)

本仓库用于发布 xAgent Server 官方二进制版本，仅包含发布包、校验文件、版本元数据和授权文件，不包含 xAgent 源代码。

当前版本：[xAgent v0.0.9.beta](https://github.com/coffeehc/xagent-releases/releases/tag/v0.0.9.beta)

使用文档：

- [xAgent 使用手册](https://xagent.xiagaogao.com/)
- [开始安装 xAgent](https://xagent.xiagaogao.com/docs/getting-started/install/)
- [xAgent 产品介绍与核心能力](https://xagent.xiagaogao.com/docs/getting-started/what-is-xagent/)
- [什么是连接器](https://xagent.xiagaogao.com/docs/getting-started/what-is-connector/)

## 什么是 xAgent

xAgent 是企业统一的 AI 工作平台。服务端部署，快速接入现有系统，权限与成本集中管控、操作全程审计；员工打开网页或手机，即可使用 AI 完成工作。实现企业可管、员工好用。

xAgent 既是员工统一使用 AI 的入口，也是企业统一管理 AI 的基座。它可以理解目标、处理资料、分析数据、生成成果、调用经过授权的工具，并连接企业现有系统继续完成工作。外部系统原有的账号和权限仍然是访问依据，xAgent 不会凭空扩大用户权限。

![xAgent 仪表板](assets/xagent-dashboard-zh.webp)

## xAgent v0.0.9.beta

本测试版重点更新：

- 新增独立的 `/admin` 管理后台和 `/admin/login` 登录入口，与 `/app` 用户端菜单和路由完全分离。
- Web 与桌面端统一为左右会话结构，主会话固定在搜索框上方，内容区在普通屏幕和超宽屏上按比例居中。
- 会话提示词即使为空也可以直接新增，保存后从下一轮起作用于主会话、Connector 会话和普通子会话。
- 表单和配置抽屉不再因误点遮罩而关闭，未保存的复杂配置不会意外丢失。
- 用户端仪表盘收敛为个人“用量统计”，模型用量直接展开；全局和按用户统计保留在管理后台。
- 会话工具栏和账号菜单进一步简化，并提供直接退出登录入口。
- 收口运行时和持久化边界，读取旧 MemoryPointer 时不改写文件，数据库 Schema 在依赖服务启动前完成初始化。

支持的平台：

- Linux AMD64
- Linux ARM64
- macOS AMD64
- macOS ARM64

完整功能变化和升级说明见[本版更新日志](changelog/v0.0.9.beta.md)。

## 安装

Linux 和 macOS 使用同一个安装命令：

```bash
curl -fsSL https://downloads.xagent.xiagaogao.com/scripts/install.sh | bash
```

安装器会自动识别平台，下载并校验对应发布包，安装或升级 xAgent，并可选择安装支持的 Connector。长期运行的服务端部署建议使用 Debian Linux 和 systemd。Windows 当前无法提供与 Linux、macOS 同等的受控脚本沙箱边界，因此暂不建议作为部署环境。

升级前请备份 xAgent 配置、数据库、工作区和 Connector 状态。部署要求和首次系统初始化流程见[开始安装 xAgent](https://xagent.xiagaogao.com/docs/getting-started/install/)。

## 手动下载

发布文件可从 [GitHub Releases](https://github.com/coffeehc/xagent-releases/releases) 下载。`v0.0.9.beta` 提供以下平台包：

```text
xagent-v0.0.9.beta-linux-amd64.tar.gz
xagent-v0.0.9.beta-linux-arm64.tar.gz
xagent-v0.0.9.beta-darwin-amd64.tar.gz
xagent-v0.0.9.beta-darwin-arm64.tar.gz
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

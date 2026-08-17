# xAgent Releases

[简体中文](README.zh-CN.md)

This repository distributes official xAgent Server binary releases. It contains
release artifacts, checksums, metadata, and licensing documents, but no xAgent
source code.

Current release: [xAgent v0.0.10.beta](https://github.com/coffeehc/xagent-releases/releases/tag/v0.0.10.beta)

Documentation:

- [xAgent Documentation](https://xagent.xiagaogao.com/en/)
- [Start Installing xAgent](https://xagent.xiagaogao.com/en/docs/getting-started/install/)
- [xAgent Product Overview](https://xagent.xiagaogao.com/en/docs/getting-started/what-is-xagent/)
- [What Is a Connector?](https://xagent.xiagaogao.com/en/docs/getting-started/what-is-connector/)

## What Is xAgent?

xAgent is the unified AI work platform for the enterprise. Deploy it on your own
servers, connect existing systems quickly, centralize access and cost controls,
and audit every action. Employees can get work done with AI from the Web or a
mobile device, giving enterprises control and employees an effortless
experience.

xAgent acts as both an AI portal for employees and an AI foundation for the
organization. It can understand goals, work with documents, analyze data,
create deliverables, call approved tools, and continue work across connected
systems. Existing system accounts and permissions remain the source of truth;
xAgent does not grant users broader access.

![xAgent dashboard](assets/xagent-dashboard-en.webp)

## xAgent v0.0.10.beta

This beta release focuses on:

- Task-aware capability preparation that keeps the existing environment for a
  continuing goal and reconciles Skills, Tools, and memory when the goal changes.
- Goal-oriented English retrieval terms for Skills, Tools, and Memory, including direct
  retrieval of standalone Tools followed by semantic capability selection.
- Platform capability self-awareness covering capability discovery, memory,
  managed secret references, Connectors, and externally or periodically triggered signals.
- Model-decided Tool use when Tools are available instead of forcing a Tool call
  on every request.
- Project-oriented session navigation and persisted collaboration between main
  and sub-sessions, including precise result delivery to the source session.
- Localized Skill Cards, accurate loaded-capability views, and a read-only
  context-cache snapshot for session diagnostics.
- Rendered Markdown, worksheet-aware spreadsheet preview, and stable standalone
  Workspace download links with retry support.
- Unified console and Agent response language preferences, expanded user-data
  formatting, and a local administrator password-recovery command.
- Safer handling of incomplete Tool arguments and output limits across OpenAI
  and compatible Providers.
- An emergency fix prevents asynchronously cleaned Session temporary files from
  blocking Session deletion; `tmp` no longer creates managed file records, and
  cleanup removes legacy records.

The release supports:

- Linux AMD64
- Linux ARM64
- macOS AMD64
- macOS ARM64

See the [release notes](changelog/v0.0.10.beta.md) for user-facing changes and
upgrade notes.

## Install

Linux and macOS use the same installer:

```bash
curl -fsSL https://downloads.xagent.xiagaogao.com/scripts/install.sh | bash
```

The installer detects the platform, downloads and verifies the matching
package, installs or upgrades xAgent, and can optionally install supported
Connectors. Debian Linux with systemd is recommended for long-running server
deployments. Windows is not currently recommended because it cannot provide the
same managed script sandbox boundary.

Before upgrading, back up the xAgent configuration, database, workspaces, and
Connector state. See the [installation guide](https://xagent.xiagaogao.com/en/docs/getting-started/install/)
for deployment requirements and first-time system setup.

## Manual Download

Release assets are available from [GitHub Releases](https://github.com/coffeehc/xagent-releases/releases).
The `v0.0.10.beta` platform packages are:

```text
xagent-v0.0.10.beta-linux-amd64.tar.gz
xagent-v0.0.10.beta-linux-arm64.tar.gz
xagent-v0.0.10.beta-darwin-amd64.tar.gz
xagent-v0.0.10.beta-darwin-arm64.tar.gz
```

The release also provides:

- `SHA256SUMS`: checksums for archives and release documents.
- `BINARY_SHA256SUMS`: checksums for the executable inside each archive.
- `release.json`: machine-readable version and licensing metadata.
- `LICENSE`, `EULA.md`, and `THIRD_PARTY_NOTICES.md`.

Each archive contains the xAgent executable, README, release metadata, and
licensing documents. It does not contain source code.

## Verify Downloads

Download the checksum files and release assets, then verify them before
installation:

```bash
shasum -a 256 -c SHA256SUMS
```

Linux users can use `sha256sum -c SHA256SUMS`. If you download only one platform
archive, compare its calculated SHA256 value with the matching line in
`SHA256SUMS`.

## Source Code and Licensing

Artifacts in this repository are binary distributions. Publishing them here
does not mean that the corresponding source code is open source. Use of the
software is governed by the `LICENSE`, `EULA.md`, and third-party notices
included with each release.

## Feedback and Security

- [Share an idea or report a general issue](https://xagent.xiagaogao.com/en/docs/cooperation/idea/)
- For security issues containing sensitive details, use the private contact
  channel described in the documentation instead of a public GitHub issue.

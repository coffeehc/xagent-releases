# xAgent Releases

[简体中文](README.zh-CN.md)

This repository distributes official xAgent Server binary releases. It contains
release artifacts, checksums, metadata, and licensing documents, but no xAgent
source code.

Current release: [xAgent v0.0.15.beta](https://github.com/coffeehc/xagent-releases/releases/tag/v0.0.15.beta)

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

## xAgent v0.0.15.beta

This beta release focuses on:

- AgentCore now owns model execution consistently, with legacy execution and
  validation paths removed.
- Session delegation carries the user's goal, input files, and explicit
  constraints without inventing font, layout, verification, or toolchain rules.
- Document creation, append, and conversion finish when the Tool succeeds;
  open-ended read, repair, and re-export loops are no longer the default.
- Word, PowerPoint, and Excel use one branded Office template system; Word
  covers and tables of contents are separated, and table text inherits the body
  font.
- PDF, PPTX, DOCX, Excel, and Mermaid previews have consistent type routing,
  with separate Mermaid handling for interactive preview and export.
- Native Excel Tools cover scoped reads and writes, append operations, tables,
  charts, recalculation, and PDF export without inlining complete workbooks.
- `fs_search_in_text` handles search within one text file, while cross-file
  retrieval uses a Session-scoped index Tool.
- Runtime Assets now synchronize, download, install, and update Catalog packages
  automatically, switching `current` atomically while retaining manual controls.
- Token estimation is calibrated for digit-heavy document content, with
  Provider-confirmed context overflow recovery as a fallback.
- Excel previews avoid repeated row loading and use a bounded, padded grid
  viewport instead of filling the entire preview window.
- Session and administration pages share more components and reduce unnecessary
  rendering across common workflows.

The release supports:

- Linux AMD64
- Linux ARM64
- macOS AMD64
- macOS ARM64

See the [release notes](changelog/v0.0.15.beta.md) for user-facing changes and
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
The `v0.0.15.beta` platform packages are:

```text
xagent-v0.0.15.beta-linux-amd64.tar.gz
xagent-v0.0.15.beta-linux-arm64.tar.gz
xagent-v0.0.15.beta-darwin-amd64.tar.gz
xagent-v0.0.15.beta-darwin-arm64.tar.gz
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

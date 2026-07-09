# xAgent Releases

[简体中文](README.zh-CN.md)

This repository publishes xAgent Server release artifacts.

It is a public binary distribution repository. Source code for the released
components may be maintained in separate repositories and is not published here
unless explicitly stated in a specific release.

## What Is Published Here

Release artifacts may include:

- xAgent Server binaries
- xAgent packages with embedded Web UI
- Deployment examples, checksums, and release notes

Connector binaries are published separately at:

<https://github.com/coffeehc/xagent-connectors>

Each release describes the exact target platforms and runtime requirements
included in that version.

## Download

Download artifacts from the GitHub Releases page:

<https://github.com/coffeehc/xagent-releases/releases>

Typical release assets may look like:

```text
xagent-linux-amd64.tar.gz
xagent-darwin-arm64.tar.gz
SHA256SUMS
```

File names and supported platforms may change by release. Always use the assets attached to the release version you intend to deploy.

## Verify Artifacts

When a release provides `SHA256SUMS`, verify the downloaded file before installation:

```bash
shasum -a 256 -c SHA256SUMS
```

On Linux, `sha256sum` can also be used when the checksum file format matches the release notes.

## Versioning

Release tags use semantic-style version names:

```text
vMAJOR.MINOR.PATCH
```

Examples:

```text
v1.0.0
v1.1.0
v1.1.1
```

Pre-release versions may use suffixes such as:

```text
v1.2.0-rc.1
v1.2.0-beta.1
```

## Compatibility

Compatibility is described per release. Before upgrading, review the release notes for:

- supported operating systems and CPU architectures
- required configuration changes
- data migration notes
- known breaking changes

## Source Code And Licensing

Artifacts in this repository are distributed as release binaries.

Publishing a binary artifact here does not by itself mean that the corresponding source code is open source. If a component has a separate source repository, license, or open-source statement, that information will be stated in the relevant release notes or documentation.

## Security

Do not report security issues through public GitHub issues if the report contains sensitive details. Use the contact channel provided by the project maintainers or the release documentation.

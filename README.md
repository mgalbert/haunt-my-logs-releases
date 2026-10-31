# Haunt My Logs — experimental Halloween MVP

Turn a bounded Splunk snapshot into a haunted soundtrack, with two tracks, A/B
effects and an inspectable histogram. Music interprets counts; it is not an
incident diagnosis or a production monitoring system.

## Download Haunt My Logs v0.9.0-rc2

**[Download the Splunk app installer (.tgz)](https://github.com/mgalbert/haunt-my-logs-releases/releases/download/v0.9.0-rc2/haunt_my_logs-0.9.0-rc2.tgz)**

[Installation instructions](releases/0.9.0-rc2/INSTALL.md) · [SHA256 checksums](https://github.com/mgalbert/haunt-my-logs-releases/releases/download/v0.9.0-rc2/SHA256SUMS) · [All release downloads](https://github.com/mgalbert/haunt-my-logs-releases/releases/tag/v0.9.0-rc2)

**Experimental prerelease:** intended for isolated testing, not production monitoring. Use an administrator-approved Splunk test instance.

## Watch the Demo

**What if you could hear anomalies in your Splunk data?**

Watch a 45-second synthetic-data demonstration of Haunt My Logs, featuring
interactive telemetry sonification, synchronized visualizations and anomaly-focused
playback.

**[Watch Demo 2 — Featured Video](https://github.com/mgalbert/haunt-my-logs-releases/releases/download/v0.9.0-rc2/Haunt-My-Logs-Demo-2-1080p.mp4)**

[Watch Demo 1 — Original Walkthrough](https://github.com/mgalbert/haunt-my-logs-releases/releases/download/v0.9.0-rc2/Haunt-My-Logs-Demo-1-1080p.mp4)

This independent distribution repository is for reviewed Haunt My Logs releases.
Development history, internal test evidence and release credentials are excluded.

## Install 0.9.0-rc2

Download the [v0.9.0-rc2 installer](https://github.com/mgalbert/haunt-my-logs-releases/releases/download/v0.9.0-rc2/haunt_my_logs-0.9.0-rc2.tgz) and [SHA256SUMS](https://github.com/mgalbert/haunt-my-logs-releases/releases/download/v0.9.0-rc2/SHA256SUMS) from the published prerelease. Follow the [installation instructions](releases/0.9.0-rc2/INSTALL.md) before installing.
GitHub's automatic Source code ZIP/tarball contains distribution-repository files;
it is not the Splunk installer. No Python, Node or source build is needed.

The installer is 13,581,469 bytes. SHA-256:
8aa8569de677b1ca05d368664e74e3febd0c39411612c17273ab73597dfa6597

See [installation](releases/0.9.0-rc2/INSTALL.md),
[requirements](releases/0.9.0-rc2/REQUIREMENTS.md),
[compatibility](releases/0.9.0-rc2/COMPATIBILITY-SUMMARY.md), and
[known limitations](releases/0.9.0-rc2/KNOWN-LIMITATIONS.md).

The exact RC2 installer was functionally tested on standalone Splunk Enterprise
10.2.8 and 10.6.1.1, Ubuntu 24.04.5 LTS at /opt/splunk, Windows Chrome 155.
This does not certify version families, other platforms or production use.
Natural timeout expiry remains unverified; the compatibility matrix retains the
installer metadata difference, launcher finding and session-isolation limits.

Important: the unchanged installer contains older embedded preparation-stage README files,
including obsolete uninstalled/10.4.x wording and missing documentation links.
Use these versioned public companion documents for current acceptance and install
guidance. The archive is preserved unchanged to match the tested checksum.

Start with the built-in Synthetic demo; it needs no index or ingestion. Native
Compose uses your existing search capability and index access. Installation is an
administrator action and can recycle Splunk Web. Use an isolated test instance.

Original code/arrangement: [MIT](LICENSE). Instrument recordings: CC0; see
[third-party notices](THIRD_PARTY_NOTICES.md), the [CC0 text](licenses/VSCO-CC0.txt)
and the [original audio notice](licenses/LICENSE-original.txt).

See the [promotion policy](docs/PROMOTION-POLICY.md) and
[security documentation](releases/0.9.0-rc2/SECURITY.md). No dedicated private vulnerability-reporting channel is currently offered.
GitHub issues are public and are not confidential. Do not post credentials, raw
logs, sensitive native captures or exploit details in public issues.

## Source and exact-byte reproduction

The installer includes readable Python/JavaScript application source and audio
provenance. Cloning this distribution repository does not reproduce the installer.
Exact compressed-byte reproduction requires **Windows CPython 3.14.6 x64 with
zlib-ng 2.2.4**, the toolchain used for the verified release reproduction. Identical
member/source bytes can compress differently on another toolchain. Matching member
hashes establishes member equivalence; it does not establish archive byte identity.
No build or publication workflow is included in this distribution repository.

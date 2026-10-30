# Haunt My Logs 0.9.0-rc2 — experimental public prerelease

Haunt My Logs turns bounded caller-authorized Splunk snapshots into Crooked Waltz
or Retro 1980s Horror Synth, with A/B effects, three playback modes, provenance and
an inspectable fictional demo. No external audio, model or analytics service runs.

For installation, use haunt_my_logs-0.9.0-rc2.tgz from Release Assets, verify
SHA256SUMS, then follow [INSTALL.md](INSTALL.md). Automatic Source code archives are not the installer.
Installer: 13,581,469 bytes; SHA-256:
8aa8569de677b1ca05d368664e74e3febd0c39411612c17273ab73597dfa6597

This is the unchanged, 39-member RC2 archive used for functional testing on
standalone Enterprise 10.2.8 and 10.6.1.1, Ubuntu 24.04.5 LTS at /opt/splunk,
embedded Python 3.13 and Windows Chrome 155. Independent counts, caller access controls,
observed running cancellation/cleanup, playback and 24 PCM cases per version
passed, with separate human listening checks for each synthetic sequence.

Natural timeout expiry remains NOT VERIFIED. Literal installed equality fails
only for Splunk-modified app.conf metadata. The 10.2.8 restricted-role launcher
exception was not reproduced on 10.6.1.1; no vendor fix is claimed. Distinct same-user
browser sessions passed only the 10.6.1.1 test and remain unverified on 10.2.8.
Effective shipped role capabilities differ. See [COMPATIBILITY-SUMMARY.md](COMPATIBILITY-SUMMARY.md) and
[KNOWN-LIMITATIONS.md](KNOWN-LIMITATIONS.md); this is not production certification or version-family support.

Embedded preparation docs have obsolete uninstalled/10.4.x wording and missing
links. Current companion files supersede them without changing tested archive bytes.
Installation can recycle Splunk Web. No new functionality or rebuilt installer is
introduced by this distribution promotion. Public v0.9.0-rc2 identifies a public
distribution commit and approved hashes, not a checkout of private development.

Original code/arrangement is MIT; recorded instruments are CC0. Read LICENSE and
THIRD_PARTY_NOTICES.md. No private development history or internal evidence is included.

## Authentication evidence correction

Unauthenticated Compose was prevented in both tested browser scenarios. The
10.6.1.1 logged-out browser check recorded HTTP **303 (redirect)**, not 401; the
10.2.8 logged-out browser check recorded 401. Independent anonymous/invalid-token
management and missing/invalid-CSRF checks recorded 401 on both versions. The
303 observation is not a claim that authentication behavior is identical across
versions or that the precise 401 was observed for that 10.6.1.1 browser check.

No dedicated private vulnerability-reporting channel is currently offered, by
explicit owner decision for this experimental MVP. GitHub issues are public and
are not confidential; do not post credentials, raw logs, sensitive native captures
or sensitive exploit details there. No reporting service or contact was configured
and no reporting capability was tested. This candidate still requires explicit
human publication approval.

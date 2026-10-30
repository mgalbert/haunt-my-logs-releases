# Independent release promotion policy

Distribution repository: mgalbert/haunt-my-logs-releases (proposed).
Release tag: v0.9.0-rc2 (proposed); mark the GitHub Release as a prerelease.
This local candidate is NOT APPROVED FOR PUBLICATION. The repository, commit,
tag and release are not created by this preparation. Their eventual public links
and anonymous downloads must be checked after separately authorized publication.

## Boundary and approval

The distribution repository starts with independent root history and only the
reviewed public-tree files. No private history, upstream remotes, development CI,
raw compatibility evidence or credentials are copied. The public tag identifies
the independent distribution commit and its approved artifact digests, not a
development-source checkout. Internal source/evidence/approval mapping remains
separate; no private repository URL or access is needed to install the release.

The installer is a Release Asset; automatic GitHub Source code archives contain
the distribution tree and are not Splunk installers. Readable application source,
original licenses and audio provenance are already in the installer. Cloning this
distribution tree does not reproduce the installer. Exact compressed-byte
reproduction requires Windows CPython 3.14.6 x64 with zlib-ng 2.2.4. Member/source
equivalence is distinct from compressed-archive byte identity.

## Promotion steps for each version

1. Freeze an installer by exact digest and member manifest. Perform qualified
   compatibility testing on those exact bytes, not a fresh replacement build.
2. Select only reviewed installer/docs/license files, omit internal history/data,
   review all text/links and keep original notices. Prepare public limitations.
3. Hash every final release payload and write SHA256SUMS excluding itself. Verify
   member hashes and identical Git-tree/asset sidecars. Bind the internal approval
   record to the exact public-tree and asset inventory digests.
4. Require explicit human approval of destination, files/digests, limitations and
   publication actions. Green CI, a source merge, a branch update or a previous
   release approval is not promotion approval. Unknown/new files stop promotion.
5. Use a manually operated publisher credential scoped only to distribution on a
   trusted operator host. Public Actions remain disabled initially. Do not grant
   public CI, deploy keys, tokens, app installations or reusable workflows access
   to private development or its secrets. No automatic private-to-public publish.
6. After approval, create the independent public commit/tag and a draft prerelease;
   upload only approved assets, redownload and verify digests before publication.
   After publication verify downloads/links anonymously and record the result.

## Changes and incident response

Never move a published tag or replace installer bytes in place. Runtime/embedded
file changes require a new candidate/version and validation. Public documentation
can receive reviewed commits; a changed downloadable sidecar set needs a distinct
documentation-revision release/tag and a new manifest/checksum approval, even if
the installer digest is unchanged. Use dated errata to explain prior claims.

Stop on hash/allowlist mismatch, secret/private data, missing rights, misleading
compatibility claims, unknown publication authority or private credential coupling.
The owner has explicitly chosen to offer no dedicated private vulnerability-
reporting channel for this experimental MVP. No reporting service/contact or GitHub
Private Vulnerability Reporting is a release prerequisite, configured capability
or tested capability. Public issues are not confidential. Preserve that disclosure
and the data-sharing restrictions in
[security documentation](../releases/0.9.0-rc2/SECURITY.md).
On incident, halt promotion, preserve private evidence, obtain authorization for
withdrawal/advisory/credential rotation as appropriate, and assume public copies
may persist. Never conceal a replacement under an old tag/digest. Installation
rollback is a separate operator action described in
[ROLLBACK.md](../releases/0.9.0-rc2/ROLLBACK.md).

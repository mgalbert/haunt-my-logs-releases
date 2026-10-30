# Install Haunt My Logs 0.9.0-rc2

Experimental prerelease; start on an isolated, authorized standalone test instance.
Read [requirements](REQUIREMENTS.md), [known limitations](KNOWN-LIMITATIONS.md),
[security](SECURITY.md) and [rollback](ROLLBACK.md) first.
Use this public companion guide instead of the archive's older preparation docs.

1. From this distribution repository's v0.9.0-rc2 Release Assets, download
   haunt_my_logs-0.9.0-rc2.tgz and SHA256SUMS. Do not install the automatic Source
   code ZIP/tarball. No build tools are needed.
2. Verify 13,581,469 bytes and SHA-256
   8aa8569de677b1ca05d368664e74e3febd0c39411612c17273ab73597dfa6597.
   Linux:

   ```sh
   sha256sum haunt_my_logs-0.9.0-rc2.tgz
   ```

   Windows PowerShell:

   ```powershell
   Get-FileHash .\haunt_my_logs-0.9.0-rc2.tgz -Algorithm SHA256
   ```

   Compare with SHA256SUMS and stop on any mismatch. With all assets downloaded,
   `sha256sum --check SHA256SUMS` verifies all eleven payload files; SHA256SUMS
   excludes itself. Check missing-file warnings if only some assets were downloaded.
3. An administrator records instance health/configuration and backups. This is a
   fresh-install guide. If haunt_my_logs already exists, stop and plan an upgrade
   separately; do not overwrite it. No prior 0.8.2 installation is required.
4. In Splunk Web choose Apps → Manage Apps → Install app from file and select the
   verified TGZ. The sole top-level directory is haunt_my_logs. Do not unpack over
   system/local or another app. Native installation may recycle Splunk Web and
   interrupt browser sessions; arrange an appropriate maintenance window.
5. Verify app/endpoint registration and health. The tested 10.2.8 and 10.6.1.1
   installations worked after install-time Web recycling without a subsequent
   full splunkd restart. Other environments may require a separately planned
   restart. Do not weaken authentication, CSRF, TLS or role/index controls.
6. Open Haunt My Logs → Listening Room → Open Haunt My Logs. Select Synthetic demo,
   Compose demo, then Play. The demo runs no native search and indexes nothing.
7. For Native caller search, use an existing authorized index and a small bounded
   UTC window. Verify counts, provenance and cleanup; changing playback does not
   dispatch a new Compose. Review effective role permissions on your version.

Splunk rewrites default/app.conf with installer metadata/formatting. The tested
installed comparison is 38/39 exact files, with code/static integrity preserved.
Keep the archive checksum as the artifact identity; do not expect all installed
files to remain byte-identical. Natural timeout expiry was not verified.

Optional indexed demonstration: the included demo/generate_fixture.py writes
fictional NDJSON locally and refuses overwrite. An authorized operator may upload
it once to an existing approved test index using sourcetype haunt:demo, then use
its printed UTC bounds within 30 days. Repeated uploads duplicate events. Cleanup
uses existing retention; no delete/index-creation action is supplied or required.

The embedded README files are historical and have missing staging/acceptance/image/
notice links. Use the public companion files. Do not modify the reviewed TGZ to
repair those links. No upgrade or rollback occurs automatically.

## Source and archive identity

This public distribution checkout is not a build checkout. Readable application
source is included in the installer. Exact compressed-byte reproduction requires
**Windows CPython 3.14.6 x64 with zlib-ng 2.2.4**. A different compressor may create
a different archive from identical members. Verify the supplied installer digest;
do not rebuild or repack it to correct its historical documentation.

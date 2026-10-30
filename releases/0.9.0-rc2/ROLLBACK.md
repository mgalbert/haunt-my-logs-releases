# Fresh-install preservation and rollback

Before installation, an authorized operator records health, app/global settings,
active jobs and suitable backups. If haunt_my_logs already exists, stop: this guide
does not authorize upgrading/overwriting it. No earlier Haunt My Logs baseline installation is required.

If the candidate fails, stop playback/use, request cancellation of its active
Compose and verify known jobs finish. Preserve sanitized failure evidence privately.
With operator authorization, use Splunk's app-management procedure to disable or
remove only haunt_my_logs. Plan Web/service effects separately; removing static
files does not prove the persistent handler is unloaded. Never remove unrelated
apps, global settings, credentials, indexes or shared Splunk runtime roots.

Preserve /opt/splunk/var/run/splunk/haunt_my_logs until no worker/job uses it. Any
later app-scoped cleanup requires exact path and shutdown checks. Optional fixture
data follows the existing index retention policy; uninstall does not delete it.
Compare health/protected configuration to preflight and investigate unexplained
differences. No uninstall, restart, data deletion or restore runs automatically.

Use [INSTALL.md](INSTALL.md) for fresh-install checks and
[KNOWN-LIMITATIONS.md](KNOWN-LIMITATIONS.md) for cleanup/resource caveats.

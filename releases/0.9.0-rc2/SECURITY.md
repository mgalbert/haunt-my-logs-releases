# Security and experimental-use scope

Native Compose runs with the authenticated caller's search capability and index
permissions, not a system/admin fallback. It accepts one literal index and a
closed Boolean expression grammar, not arbitrary SPL pipelines. Authentication,
POST exposure and normal Splunk Web session/CSRF checks remain required.

Bounds: 2–60 minutes within 30 days, UTC-aligned 30-second buckets, up to 120
buckets, 100,000 matching events and 100,000 monitored scanned events, native
max_time=10 seconds, application deadline=12 seconds plus cleanup, 256 KiB response
checks. Monitoring may overshoot; body-size checks occur after receipt. These are
not certified physical I/O, memory or end-to-end wall-clock ceilings. Natural
timeout expiry remains unverified in the installed tests.

Private runtime: /opt/splunk/var/run/splunk/haunt_my_logs, directory 0700 and records
0600. Operation identity includes hashed caller/session and random operation ID.
Known-SID cleanup is attempted. Unknown dispatch SIDs depend on native limits/TTL;
crashed running records may require operator maintenance. One shared app lease
provides no per-user fairness or hostile-tenant availability guarantee.

Only aggregates return to the app, but search strings, conditions, usernames,
counts and costs may be sensitive. Native negative-auth/CSRF logs can contain key
material. Do not share raw logs, HAR, cookies, native captures or local config.
Use fictional demo data for public examples. Static app assets are public by design.

## Tested boundaries and remaining limits

Caller authorization, index filtering, cross-user operation isolation and native
job ACL checks passed in the two exact environments in
[COMPATIBILITY-SUMMARY.md](COMPATIBILITY-SUMMARY.md). A blocked index returned zero
events under native index access controls, not an app-generated index-denial 403.
Distinct same-user session isolation passed for the tested independent browser
contexts on 10.6.1.1; it remains NOT VERIFIED on 10.2.8. Sharing the same session
token is not an isolation boundary.

Installed all-member byte equality failed on both versions because Splunk adds
installer metadata/formatting to default/app.conf. The other 38 files, including
code/static assets, matched. A restricted-role launcher console exception occurred
on 10.2.8 and was not reproduced on 10.6.1.1; effective default role capabilities
differ, so no vendor fix is claimed. Do not broaden permissions as a workaround.

Use only trusted-user standalone experimentation. Shared-instance resource
availability is not assured: scan counts can overshoot, the shared lease has no
fairness/rate limiting and unknown-SID cleanup depends on native limits. Natural
timeout expiry remains NOT VERIFIED. Read [KNOWN-LIMITATIONS.md](KNOWN-LIMITATIONS.md).
This is not production, AppInspect or Splunkbase certification.

## Vulnerability reporting and public issues

No dedicated private vulnerability-reporting channel is currently offered for
this experimental MVP. The owner has explicitly chosen not to implement GitHub
Private Vulnerability Reporting or establish a dedicated reporting service or
contact address for this release. This is a scope decision, not evidence that a
reporting capability was tested or enabled.

GitHub issues are public and are not confidential. Do not post credentials,
session cookies, tokens, raw native logs, sensitive search strings or snapshots,
customer data or sensitive exploit details in public issues. The absence of a
dedicated private reporting channel is a disclosed limitation of this MVP.

# Known limitations — 0.9.0-rc2

- Experimental Halloween MVP; no production, AppInspect or Splunkbase certification.
- Functionally tested only in the exact environments in [COMPATIBILITY-SUMMARY.md](COMPATIBILITY-SUMMARY.md).
  Natural native runtime/application deadline expiry remains NOT VERIFIED on both.
  Code configures native max_time=10 seconds and an app deadline of 12 seconds;
  cleanup can add time and these are not a certified wall-clock/resource ceiling.
- Scanned-event monitoring can overshoot. One composition lease is shared by the
  app instance, without per-user fairness/rate limiting or cluster-wide quotas.
  Lost dispatch responses can leave an unknown SID subject to native limits/TTL;
  crashed running operation records may require authorized app-scoped maintenance.
- Literal installed-byte equality failed on both versions because Splunk rewrites
  default/app.conf installer metadata. All other 38 files and executable/static
  integrity passed; the supplied archive remains unchanged.
- A restricted-role launcher console exception reproduced on 10.2.8 and bundled
  Search; standalone app functionality worked. It was not reproduced on 10.6.1.1.
  No vendor fix is established; effective shipped role defaults differ. Do not
  grant admin or broader index access to hide shell warnings.
- Distinct same-user session isolation remains NOT VERIFIED on 10.2.8. It passed
  for two independently authenticated browser contexts on 10.6.1.1. Cross-user
  operation and native job ACL checks passed separately on both.
- The unchanged installer contains historical embedded preparation/uninstalled/10.4.x wording and
  five absent README links (staging, RC1 acceptance, two images, third-party notice).
  Current public companion files supersede that historical documentation; actual
  MIT/CC0/audio notices are included in the archive and surfaced publicly.
- Playback uses completed aggregate snapshots, not live monitoring or incident
  diagnosis. Musical intensity is relative within a snapshot. Independent A/B
  matches overlap; their sum is not a unique-event total. Effects refer to buckets.
- Human listening confirmation covers the installed synthetic tracks/effects per
  version, not every native mode/device/browser. User activation is required;
  hiding the page pauses playback. Settings changes can have a brief graph-change
  gap; effect tails are fixed. No mobile/Safari/Firefox lifecycle certification.
- Fictional indexed uploads are optional/manual and not idempotent. Retention
  governs cleanup; uninstall does not delete events. Native search strings,
  identities, counts and costs can be sensitive; do not publish native captures.

## Vulnerability reporting scope

No dedicated private vulnerability-reporting channel is currently offered. The
owner has chosen not to implement GitHub Private Vulnerability Reporting or a
dedicated reporting service/contact address for this experimental MVP. No such
capability was tested or enabled. GitHub issues are public and are not confidential;
do not post credentials, cookies, raw logs, sensitive native captures, customer
data or sensitive exploit details there.

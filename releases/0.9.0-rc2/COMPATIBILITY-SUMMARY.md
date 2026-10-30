# RC2 functional compatibility — qualified summary

Artifact: haunt_my_logs-0.9.0-rc2.tgz, 13,581,469 bytes, SHA-256 `8aa8569de677b1ca05d368664e74e3febd0c39411612c17273ab73597dfa6597`. Both reports tested these same bytes, not a later packaging-branch build.

| Environment | Splunk 10.2.8 | Splunk 10.6.1.1 |
|---|---|---|
| Enterprise build | 981c2d735e4d | b2ae2962645c |
| Hosting | Standalone Ubuntu 24.04.5 LTS x86-64; /opt/splunk | Same OS/prefix, independent fresh installation |
| Kernel | 6.8.0-147-generic | 6.8.0-147-generic |
| Resources | 4 vCPU, 16 GiB RAM, 100 GiB growable disk; AVX/SSE4.2/AES-NI | Same resources/features |
| Service/Python | Unprivileged Splunk account; embedded Python 3.13 persistconn | Same runtime model |
| License | Valid Enterprise download trial during tests | Independent valid Enterprise download trial |
| Browser | Windows Chrome 155.0.8059.82 | Windows Chrome 155.0.8059.82 |
| Test date | October 30, 2026 | October 30, 2026 |
| Lifecycle | Fresh installation from clean baseline | Clean baseline restored, new installation; not an upgrade of 10.2.8 |

## Side-by-side results

PASS applies only to the executed scenario. FAIL retains a failed check. NOT VERIFIED remains unobserved/inconclusive.

| Scenario | 10.2.8 | 10.6.1.1 |
| --- | --- | --- |
| Exact archive/39 manifest members | PASS | PASS |
| Literal installed member equality | FAIL: 38/39 | FAIL: 38/39 |
| Executable/static file integrity | PASS | PASS |
| Fresh native install/app/endpoint | PASS | PASS |
| Native Compose without subsequent full daemon restart | PASS | PASS |
| Install-time Web recycle | Observed | Observed |
| Launcher opens app / standalone assets | PASS | PASS |
| Clean restricted-role launcher console | FAIL | PASS: exception not reproduced |
| Synthetic independent counts | PASS | PASS |
| Indexed independent counts/UTC bounds | PASS | PASS |
| Native caller job ownership | PASS | PASS |
| Anonymous/invalid-token auth | PASS: 401 | PASS: 401 |
| Logged-out browser cannot Compose | PASS: 401 | PASS: logged-out Compose prevented; HTTP 303 redirect recorded |
| Missing/invalid CSRF | PASS: 401 | PASS: 401 |
| POST only | PASS: GET 405 | PASS: GET 405 |
| No search capability | PASS: 403 | PASS: 403 |
| Restricted index filtering | PASS | PASS |
| Cross-user operation isolation | PASS: 404 | PASS: 404 |
| Native SID read/cancel ACL | PASS: 403 | PASS: 403 |
| Operation-ID replay rejection | PASS: 409 | PASS: 409 |
| Distinct same-user browser sessions | NOT VERIFIED | PASS, tested contexts |
| Actual in-flight cancellation | PASS, attempt 2 | PASS, attempt 2 |
| Completed/cancelled search cleanup | PASS | PASS |
| Invalid input / retained snapshot | PASS | PASS |
| Two tracks, A/B effects, three modes | PASS | PASS |
| Volume/preview/pause/resume/seek/replay | PASS | PASS |
| Zero playback-only Compose requests | PASS | PASS |
| PCM correctness | PASS: 24 cases | PASS: 24 cases |
| Human listening | PASS, limited synthetic sequence | PASS, separate synthetic sequence |
| Natural runtime/deadline expiry | NOT VERIFIED | NOT VERIFIED |
| Health/config preservation | PASS within measured scope | PASS within measured scope |
| Full unqualified acceptance | NOT VERIFIED | NOT VERIFIED |

The two versions were installed and tested independently from a clean baseline,
sequentially on the same disposable resources. No upgrade of the previous Splunk
installation or restored indexed fixture established the second result.

## Count, cancellation and listening scope

The indexed fixture had 34 fictional events, with 32 inside the selected five-minute
interval, 18 A matches, 14 B matches and overlap 9. Ten 30-second buckets, including
two zero buckets and start-inclusive/end-exclusive boundary sentinels, agreed with
independent row counts and a separate native stats check. Unique A-or-B is 23;
independent A+B=32 includes overlap. The built-in synthetic demo independently
yielded 272 events, A31/B24/overlap2 and 30 buckets with zero native requests.

The second cancellation attempt on each version observed a native RUNNING job
with isDone=false, received cancel=true, then Compose 409 user_cancelled and SID
404. The first attempts completed before cancellation and are not counted as
in-flight-cancellation passes. Final fixture job inventories were empty.

Both versions passed 24 installed-module PCM cases: finite output, peak below
0.98, exact master-mute silence and replay/seek differences within 3/32768. Each
version also had a separate human confirmation of both tracks and A/B effects in
the installed synthetic sequence. That listening scope does not cover every native
mode, device or browser. Playback-only controls issued zero extra Compose calls.

## Limits retained

1. Natural native max_time/application deadline expiry was NOT VERIFIED on both.
   The tiny fixture finished well below the limits. Configured bounds and observed
   cancellation are not a direct natural-timeout test or wall-clock guarantee.
2. Literal installed-file equality remains FAIL on both: Splunk adds installer
   checksum/formatting to default/app.conf, leaving 38/39 members byte-identical.
   Code/static integrity and immutable archive hashes passed. Do not weaken the
   literal result to PASS or rewrite the approved archive.
3. Restricted-role launcher console Object exception reproduced on 10.2.8 and
   bundled Search; the standalone app page was clean. It was not reproduced on
   10.6.1.1. Denied shell requests remain. No vendor root cause/fix is established.
4. Distinct same-user browser sessions remain NOT VERIFIED on 10.2.8: repeated
   REST login returned the same token. On 10.6.1.1, independent browser contexts
   had distinct HTTP-only session cookies, own successful compositions and cross-
   operation status/cancel responses of 404. Do not generalize beyond that scope.
5. Effective shipped role defaults differ. On 10.6.1.1 the dedicated roles also
   inherited edit_own_objects, list_all_objects, run_collect, run_mcollect and
   schedule_rtsearch from shipped defaults. No operator broadening was used.
   Treat these differences as a confound in version-only launcher comparisons.
6. Logged-out Compose was prevented. The 10.6.1.1 browser recorded HTTP 303 redirect;
   the 10.2.8 browser recorded 401. Separate management authentication and missing/
   invalid-CSRF checks returned 401 on both. Do not claim the specific 10.6.1.1
   logged-out browser check observed 401.
7. No Cloud, Windows Splunk hosting, alternate prefix, forwarder, cluster, hostile
   multi-tenant production, arbitrary SPL or live-streaming support is established.
   Other browsers/mobile audio are unverified. Earlier RC1 testing on 10.4.3 does
   not certify RC2 on 10.4.x. Full unqualified acceptance remains NOT VERIFIED.

The unchanged installer contains obsolete preparation/uninstalled/10.4.x wording
and five missing README links. These public companion files provide the current
qualified record. This is an experimental Halloween MVP, not production, AppInspect
or Splunkbase certification. See [KNOWN-LIMITATIONS.md](KNOWN-LIMITATIONS.md) and
[SECURITY.md](SECURITY.md) for shared-instance availability and data-handling risks.

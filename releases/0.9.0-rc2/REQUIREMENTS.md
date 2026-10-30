# Requirements and tested scope

Experimental standalone Splunk Enterprise app, installed at /opt/splunk on Linux.
Exact tested builds: 10.2.8 (981c2d735e4d) and 10.6.1.1 (b2ae2962645c), each on
Ubuntu 24.04.5 LTS x86-64, kernel 6.8.0-147-generic, 4 vCPU/16 GiB RAM, using
embedded Python 3.13 and Windows Chrome 155.0.8059.82. These are test resources,
not established minimum sizing. See [compatibility](COMPATIBILITY-SUMMARY.md) for the complete qualified matrix.

Administrator permission is required for installation. Native Compose needs the
caller's existing search capability and permitted index; it does not use an admin
or system token. Inspect effective role defaults on the actual Splunk version.
Browser requires JavaScript, Web Audio, ES modules, secure random operation IDs,
normal Splunk session/CSRF support, user activation and an audio output device.
Use normal authenticated deployment transport; do not disable TLS/security.

The demo runs without a native index/search. No pip/npm runtime dependency,
inference service, external audio/CDN, additional port or database is installed.
Natural runtime/deadline expiry remains unverified. Registration permits Python
3.9/3.13 but installed evidence here is 3.13 only.

Not validated/supported for this MVP: Splunk Cloud, forwarders, clustered hosting,
Windows Splunk hosting, alternate install prefixes, arbitrary SPL, real-time
streaming, hostile multi-tenant workloads or other browser/mobile audio lifecycles.
RC1's historical 10.4.3 testing is not RC2 compatibility evidence for 10.4.x.

These tested environments establish narrow functional compatibility, not minimum
production capacity or a recommendation for untrusted multi-tenant use.

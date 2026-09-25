# bolt-defend-signatures

Signature releases for [bolt-defend](https://github.com/AdminBolt/bolt-defend),
adminBolt's malware detection engine.

A scheduled job (`.github/workflows/feed.yml`) builds one release a day:
hashes of known PHP malware and bolt-defend's patterns, tested against a
clean corpus (WordPress and popular plugins, Laravel, Drupal, Joomla) so
nothing that matches clean code is published, and signed. Only signatures
are published here, never malware samples.

Servers fetch the newest release from

    https://github.com/AdminBolt/bolt-defend-signatures/releases/latest/download

and install it only when `manifest.json` verifies against `feed.pub` and
every file matches the manifest. To check a release by hand:

```bash
minisign -Vm manifest.json -x manifest.json.minisig -p feed.pub
```

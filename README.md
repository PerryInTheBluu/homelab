# My Homelab

*Self-hosted infrastructure as a learning project — Pius J. Dischinger, 7th-semester Clean Energy Processes student at FAU Erlangen-Nürnberg*

## Why

I learn by building. After five Jugend forscht participations (Germany's youth research competition, mostly with awards), the habit stuck: when something annoys me, I build the fix myself. My homelab is the current incarnation of that, a private infrastructure I depend on daily. Currently I am its only user; my family will join as soon as it runs stable on hardware that is no longer at its limit.

## Architecture at a glance

- **Homeserver** (main node): repurposed office PC, i5-7400, DDR4, Linux, currently at its RAM limit, upgrade in progress (used rack server with ECC + IPMI planned)
- **Backup server**: old DDR3 gaming PC, offsite
- **Tailnet**: self-hosted Headscale on a rented VPS, domain via Cloudflare, zero open ports on any home network, zero-trust overlay for all devices
- **Client fleet**: Linux desktop and laptop, GrapheneOS phone, Android tablet, PocketBook e-reader
- **Smart home**: Home Assistant with Zigbee dongle, lights, temperature/humidity sensors, heater thermostats, door/window sensors
- **IoT tinkering**: Arduino Nano as a USB-to-IR bridge, emulating my stereo's remote, the server controls the speakers as an audio endpoint

## Services

Running in production: Nextcloud (my cloud, family access planned), Paperless (document archive), Vaultwarden (passwords), Pi-hole (DNS, incl. one for a friend on a Raspberry Pi), Joplin (notes), Raspotify (audio streaming to speakers), Home Assistant, KDE Connect bridge tooling.

**Paused, waiting for RAM:** Immich (photo library), Jellyfin (media), OctoPrint (3D printer server), KoReader + Calibre sync (e-book library to phone, laptop, tablet, e-reader), CWA.

This list is the honest state of the lab: I run into the hardware ceiling, prioritize, and document it. The server upgrade is the fix.

## Software projects born from the lab

**Cross-Device Clipboard &amp; Network Bridge** (Kotlin, Android SDK, Bash, TCP/IP): zero-latency screenshot pipeline from my Linux desktop to my tablet over Tailscale. Foreground service with inotify file watching and network callbacks that survives OEM background killers, TCP health checker for KDE Connect with endpoint caching and actionable status alerts, OOM-safe bitmap pipeline with TTL-based storage GC.

**Time tracking app with self-hosted sync backend** (Kotlin multi-module, Room, Hilt; Python/PostgreSQL/Docker server): started as a public fork of Razeman's Simple Time Tracker, which I extended into a full offline-first sync setup, with token auth, DB migrations, push/pull endpoints with deterministic conflict resolution and audit log, encrypted credentials in Android Keystore, no Google Play Services (GrapheneOS-compatible), Caddy reverse proxy with TLS inside the isolated Tailnet, pytest + smoke-test CI.

**Smaller builds**: OCID key + nRF USB dongle emulation for university login, Arduino IR bridge (above), RAM configuration debugging on the new server board (ongoing).

## Next steps

- Rack server with ECC RAM + IPMI as new main node: Proxmox, OPNsense VM (router and NAS on one box), ZFS storage tiers on SSD/NVMe, 10G SFP+ uplink
- Update rollouts with Ansible and Watchtower
- Restart the paused services with headroom to spare

## Links

- GitHub: github.com/PerryInTheBluu
- Contact: [mail@piusdischinger.com](mailto:mail@piusdischinger.com)

<h1 align="center">SCADABLE</h1>
<p align="center"><em>Your hardware fleet, managed from your codebase.</em></p>

<p align="center">
  <a href="https://scadable.com">scadable.com</a> ·
  <a href="https://docs.scadable.com">docs.scadable.com</a> ·
  <a href="https://dashboard.scadable.com">dashboard.scadable.com</a>
</p>

---

SCADABLE is the infrastructure layer between connected hardware and the cloud. Medical, industrial, energy, and ag-tech teams use it to ship a connected product without becoming a cloud company — push firmware to your repo, the fleet rolls out, telemetry streams in, and a PR opens when something needs fixing.

## What you get on day one

- **Faster time-to-market.** Skip the 12–18 month detour of building your own IoT stack. Push a tag in the repo you already have; SCADABLE builds, signs, and ships the firmware to every device in the fleet.
- **Lower operational risk.** mTLS per device, automatic certificate rotation (EST), signed OTA with A/B partitions, post-OTA diagnostic verification, and auto-rollback if any sensor health check fails. The scariest thing you ship — firmware updates — becomes boring.
- **Compliance-ready by default.** SOC 2-aligned immutable audit log (13-month retention), per-tenant isolation, FDA cybersecurity-compatible patterns, HIPAA-compatible architecture. Designed for the hospital procurement review, not against it.

## What SCADABLE actually does

You write firmware in your language — C, C++, Rust, Arduino — and link [`libscadable`](https://github.com/scadable/libscadable). You push to GitHub. The SCADABLE GitHub App reads your `.scadable/` config, builds and signs a release, and rolls it out to the fleet.

Devices come online over mTLS. Telemetry streams through the platform's MQTT broker into the time-series historian. Logs, metrics, and live diagnostics show up in the dashboard at [dashboard.scadable.com](https://dashboard.scadable.com). Every state change is recorded in an immutable audit log.

After every OTA, the platform runs the diagnostics you declared in `.scadable/diagnostics/*.yaml` against each gateway in the rollout. If `motor_health` fails on one device out of a thousand, the release is marked `verification_failed` and that gateway auto-rolls back to the previous good firmware — before the bad release reaches the rest of the fleet.

ESP32 and ESP32-S3 are production today. Linux gateways (x86_64, aarch64, armv7) for industrial Debian boxes, Raspberry Pi, and edge servers ship from `gateway-linux`. RTOS targets are on the roadmap.

## Deployment-ready in minutes

Everything you need to operate a connected hardware fleet, working out of the box:

- mTLS device identity and automatic certificate rotation (EST `simplereenroll`)
- Signed OTA with A/B partition rollback
- Post-OTA diagnostic verification with auto-rollback on failure
- MQTT broker with topic-level ACLs and offline telemetry buffering
- Time-series historian with retention rules
- SOC 2-aligned immutable audit log (13-month retention)
- Multi-tenant isolation, multi-cluster ready from day one
- Web dashboard with live telemetry, OTA controls, diagnostic runs, audit history
- GitHub App integration — push a tag, fleet rolls out

The fast path:

```bash
pip install scadable
scadable verify          # validate your .scadable/ config
```

Connect your repo via the [SCADABLE GitHub App](https://github.com/apps/scadable), pick a starter ([arduino-platformio-starter](https://github.com/scadable/arduino-platformio-starter)), push a tag, watch the fleet update.

## Public repositories

| Repository | What it is |
| :--- | :--- |
| [**libscadable**](https://github.com/scadable/libscadable) | The C library devices link against. ESP-IDF Component Registry: `crypto-a/libscadable` |
| [**arduino-platformio-starter**](https://github.com/scadable/arduino-platformio-starter) | Fastest path to a first device. PlatformIO + Arduino, `.scadable/` pre-wired |
| [**gateway-provisioning**](https://github.com/scadable/gateway-provisioning) | In-browser WebSerial flasher and captive-portal provisioning for new gateways |

Service code (broker, control plane, dashboard, historian, orchestrator) lives in private repos. The [docs at docs.scadable.com](https://docs.scadable.com) are the public reference.

## Links

- **Marketing site:** [scadable.com](https://scadable.com)
- **Documentation:** [docs.scadable.com](https://docs.scadable.com)
- **Dashboard:** [dashboard.scadable.com](https://dashboard.scadable.com)
- **Talk to us:** [cal.com/rahbaral/quick-chat](https://cal.com/rahbaral/quick-chat)

## Contributors

SCADABLE began as a university course project. The platform has evolved substantially since then — different architecture, different market, different product — but the original team's work seeded what SCADABLE is today, and they deserve credit for it.

| Full Name | GitHub Username | GitHub Profile |
| :--- | :--- | :--- |
| **Ali Rahbar** | `crypto-a` | [View Profile](https://github.com/crypto-a) |
| **Christopher Li** | `ChristopherLi05` | [View Profile](https://github.com/ChristopherLi05) |
| **Neyl Nasr** | `Lakssito` | [View Profile](https://github.com/Lakssito) |
| **Benjamin Gavriely** | `Benjamin-Uoft` | [View Profile](https://github.com/Benjamin-Uoft) |
| **Matteo Gentili** | `MatteoGentili24` | [View Profile](https://github.com/MatteoGentili24) |
| **Azaria Kelman** | `azariak` | [View Profile](https://github.com/azariak) |
| **Daniel Rafailov** | `danielrafailov1` | [View Profile](https://github.com/danielrafailov1) |

<p align="center">
  <a href="https://scadable.com">scadable.com</a> ·
  <a href="https://docs.scadable.com">docs.scadable.com</a> ·
  <a href="https://dashboard.scadable.com">dashboard.scadable.com</a>
</p>

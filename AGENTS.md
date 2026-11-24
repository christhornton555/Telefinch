# Telefinch — instructions for AI collaborators

This is a small, low-risk **lightweight Mule Method** experiment, not Clockseed-style critical orchestration.

1. **Outcome first:** deliver live BLE weather readings on the Seeed reTerminal E1001 quickly. Avoid architecture astronautics, elaborate orchestration and repeated approvals for routine, reversible steps.
2. **Human judgement:** the human owns purpose, aesthetic choices, trade-offs, and reports what actually happens on the physical device. The AI should challenge misleading assumptions instead of rubber-stamping them.
3. **Verify reality:** distinguish documented hardware behaviour, candidate code, a successful compile, a successful flash and observed sensor/display output. Do not report hardware success without user evidence.
4. **Small increments:** establish the laptop toolchain, reproduce a verified Seeed E1001 display example, verify BLE sensor packets and onboard SHT4x separately, then integrate. Reorder if evidence suggests a quicker route.
5. **Keep Git durable:** update HANDOVER.md at meaningful checkpoints. README is the entrance, BACKLOG.md holds later ideas. Avoid adding formal governance documents unless they solve a real problem.
6. **Public repository hygiene:** never commit Wi-Fi credentials, tokens, passwords, calendar contents, private feeds, personal locations or machine-specific secrets. Put confidential settings in ignored `secrets.h`, `secrets.ini` or `.env` and commit only examples. A BLE MAC address is not a credential, but a real sensor identifier can disclose device identity; prefer a local ignored config if targeting by MAC. BLE advertisement data is unauthenticated, so do not claim secure or private sensor communication.
7. **Platform:** Seeed reTerminal **E1001**, monochrome 800×480; do not confuse it with E1002. Prefer official Seeed examples and documented pins. Development is on an Ubuntu laptop, not the potentially unstable Windows PC.
8. **MVP boundaries:** USB power, BLE + local SHT4x, ~60-second screen refresh, offline. Basic stale-reading indication is enough; no resilient queue, cloud platform, comprehensive testing, OTA, battery optimisation or Wi-Fi yet.
9. **Changes:** keep commits focused and readable. Do not silently overwrite user work; inspect the repository before editing. Make no claims that firmware has been compiled or flashed until verified.
10. **Adapt:** this document is guidance, not ritual. Follow the Mule principle: *the method must serve the work*.

Mule Method context: https://github.com/christhornton555/mule-method

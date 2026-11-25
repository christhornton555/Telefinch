# Telefinch

*A small, quiet household information display.*

Telefinch is an open-source, offline-first e-paper dashboard for the **Seeed Studio reTerminal E1001** (ESP32-S3; 800 × 480 monochrome display). Like its namesake bird, it quietly brings information from the outside world into the home.

**Status (25 November 2026):** paused at M0 pending USB enumeration on another computer. Factory Wi-Fi dashboard deployment works; no custom firmware has been built, flashed or tested.

## MVP

Display a nearby RuuviTag's outdoor temperature, humidity and pressure over Bluetooth Low Energy, alongside the E1001's onboard SHT4x indoor temperature/humidity readings. Update the display approximately once per minute. Initially USB-powered, completely offline.

Success means **real sensor data appearing on the physical display**, not simply compiled code.

## Our lightweight Mule Method

- Human defines goals and verifies hardware results; AI researches, implements and makes assumptions visible.
- Work in small testable increments; avoid process overhead, elaborate architecture and repeated low-value approvals.
- GitHub preserves the useful context in [AGENTS.md](AGENTS.md), [HANDOVER.md](HANDOVER.md), and [BACKLOG.md](BACKLOG.md). The project need not implement every element of Mule Method's provisional template.
- Source code is public. Do not commit passwords, keys, Wi-Fi credentials, private locations or identifying sensor MAC addresses.
- This is an experiment in right-sized collaboration, not a ratified Mule Method standard.

## Start here

Read [HANDOVER.md](HANDOVER.md) for the restart checklist and USB diagnostic history. The current development laptop runs Windows 10; VS Code and the PlatformIO extension are installed. Resume with USB enumeration on an independent computer before attempting a flash.

## Useful references

- [E1001 getting started](https://wiki.seeedstudio.com/getting_started_with_reterminal_e1001/)
- [Seeed E Series Arduino display cookbook](https://wiki.seeedstudio.com/reterminal_e10xx_with_arduino/)
- [Seeed onboard peripherals cookbook](https://wiki.seeedstudio.com/reterminal_e10xx_with_arduino_peripherals/)
- [Seeed PlatformIO guide](https://wiki.seeedstudio.com/epaper_work_with_platformio/)
- [Seeed E1001 GxEPD2 display example](https://github.com/Seeed-Projects/Seeed_GxEPD2/tree/master/examples/GxEPD2_reTerminal_E1001)
- [Ruuvi RAWv2 protocol](https://docs.ruuvi.com/communication/bluetooth-advertisements/data-format-5-rawv2)

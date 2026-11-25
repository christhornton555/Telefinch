# Telefinch — handover

**Updated:** 25 November 2026
**Stage:** M0 paused by human decision — USB enumeration blocker.
**State:** GitHub repository initialised and local clone verified by user. Factory Wi-Fi dashboard deployment successful (user report). PlatformIO extension installed; core/build not verified. No custom firmware compilation, flash or sensor decoding yet.

## Project and intent
- A pleasant, passive e-paper information display named **Telefinch**.
- Device: **Seeed Studio reTerminal E1001** (800×480 monochrome e-paper, ESP32-S3 with BLE and Wi-Fi). Factory screen seen: SenseCraft HMI Wi-Fi setup prompt.
- External sensor: RuuviTag with firmware reported as **Ruuvi FW v3.31.1+default**; BLE readings previously observed from an Android phone. Format 5/RAWv2 expected, not yet confirmed by this ESP32.
- Sensor identity/target: store local identifier privately if needed; do not embed its real MAC in public repository.
- Internal sensor: E1001 SHT4x temperature/humidity over I²C, documented by Seeed; not yet read.
- Development: Windows 10 laptop (corrected from earlier Ubuntu assumption). Main PC stability work takes priority.
- Goal: visible live outdoor temperature/humidity/pressure and indoor temperature/humidity; periodic ~60-second display update; USB-powered and offline.

## M0 evidence (24–25 November 2026)
- Windows 10 laptop, VS Code 1.136.0, Python 3.14.7, Git 2.45.0.windows.1.
- PlatformIO IDE extension 3.3.4 and C/C++ extension 1.35.6 installed successfully; PlatformIO core and compiler not yet verified.
- Local clone was clean and synchronised at a541717 before this checkpoint.
- E1001 boots, charges via USB, connects to Wi-Fi and successfully installs a SenseCraft gallery dashboard (user reports).
- USB: no COM ports returned by Get-PnpDevice or [System.IO.Ports.SerialPort]::GetPortNames(); before/after PnP comparison returned no new devices. Device Manager showed no visible tree change and no Windows connection sound.
- Supplied cable and known working laser-cutter data cable tested; both laptop USB ports tested. Boot, refresh and long-press refresh tested. WCH CH340 driver installation made no difference.
- Root cause remains unknown. Charging and working factory firmware do not exclude a fault in the separate USB data path; Windows/driver issues are also not excluded.
- No supported initial arbitrary-firmware OTA route was identified in the Seeed documentation reviewed during discussion. SenseCraft dashboard deployment is not equivalent to custom firmware flashing. Do not assume undocumented methods are impossible.

## Restart checklist
1. Resume when the human chooses, after higher-priority PC stability work.
2. Pull latest main in the local clone (git pull --ff-only).
3. Test USB enumeration on a second computer, ideally Windows 11 desktop once stable or Linux if available. Try both USB-C orientations if not already done. No development tools required for enumeration.
4. Windows: run [System.IO.Ports.SerialPort]::GetPortNames() and inspect Device Manager before/after plugging in. Linux: compare lsusb and check /dev/ttyUSB* and /dev/ttyACM*.
5. If no enumeration on independent hosts with a known-good data cable, contact Seeed support with the evidence. Do not open the device or attempt unsupported flashing as a default.
6. Once serial works, verify PlatformIO core/build, confirm factory recovery route, flash the official E1001 display example and proceed to M1/M2.
7. Prioritise basic authenticated, opt-in OTA after initial USB flashing; preserve offline MVP functionality.

While paused, the human may explore SenseCraft gallery dashboards for design inspiration; no requirement to do so.

## MVP stages
1. **M0:** environment and device serial port identified, factory recovery route noted.
2. **M1:** Ruuvi format-5 payload received and decoded; onboard SHT4x read (serial output acceptable).
3. **M2:** real values rendered on E1001; basic 60-second refresh. *MVP complete when visually confirmed on device.*

Sequence can change if official examples make another route faster.

## References and constraints
- Seeed E1001-specific GxEPD2 display example: https://github.com/Seeed-Projects/Seeed_GxEPD2/tree/master/examples/GxEPD2_reTerminal_E1001
- Seeed display guide: https://wiki.seeedstudio.com/reterminal_e10xx_with_arduino/
- Seeed onboard peripherals: https://wiki.seeedstudio.com/reterminal_e10xx_with_arduino_peripherals/
- Seeed PlatformIO: https://wiki.seeedstudio.com/epaper_work_with_platformio/
- Ruuvi RAWv2: https://docs.ruuvi.com/communication/bluetooth-advertisements/data-format-5-rawv2
- Minimal features now; future features in BACKLOG.md. Treat untested code as untested.
- Do not store secrets or identifying sensor addresses in this public repository.

## Mule Method observation (provisional)
This is a **low-risk lightweight variant** of the current collaboration baseline, not a new standard. The planning conversation and physical testing guide development; Git preserves concise context. Evaluate whether this small documentation footprint actually helps rather than turning the method itself into the deliverable.

### Observation — responding to a blocker (25 November 2026)
The human chose to pause rather than spend disproportionate effort on a low-risk project while another priority needs attention. The AI initially assumed Ubuntu and issued incompatible commands; the human corrected the OS, and subsequent diagnostics used PowerShell. Human testing established useful positive and negative evidence, but the cause was not resolved. Preserve the distinction between failure to achieve MVP and failure of the collaboration process. The human suggested that examining responses to failure may yield more insight for Mule Method than a frictionless success. Review later whether the lightweight handover enables efficient restart, whether the diagnostic effort was proportionate, and whether the initial environment assumption could have been avoided. This is an observation, not a validated general rule.

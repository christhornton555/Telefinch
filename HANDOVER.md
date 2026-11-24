# Telefinch — handover

**Updated:** 24 November 2026
**Stage:** repository initialisation / environment checks outstanding.
**Verified state:** GitHub repository created, public and writable. Hardware has **not** been accessed from this session. No toolchain install, compilation, USB connection, firmware flash or sensor decoding has been verified.

## Project and intent
- A pleasant, passive e-paper information display named **Telefinch**.
- Device: **Seeed Studio reTerminal E1001** (800×480 monochrome e-paper, ESP32-S3 with BLE and Wi-Fi). Factory screen seen: SenseCraft HMI Wi-Fi setup prompt.
- External sensor: RuuviTag with firmware reported as **Ruuvi FW v3.31.1+default**; BLE readings previously observed from an Android phone. Format 5/RAWv2 expected, not yet confirmed by this ESP32.
- Sensor identity/target: store local identifier privately if needed; do not embed its real MAC in public repository.
- Internal sensor: E1001 SHT4x temperature/humidity over I²C, documented by Seeed; not yet read.
- Development: Ubuntu laptop. Main Windows PC is unstable and undergoing backup, so keep work independent from it.
- Goal: visible live outdoor temperature/humidity/pressure and indoor temperature/humidity; periodic ~60-second display update; USB-powered and offline.

## Next action — collect environment evidence
On the Ubuntu laptop with the E1001 connected via USB-C:
```sh
lsb_release -ds
python3 --version
git --version
code --version
lsusb
ls -l /dev/ttyUSB* /dev/ttyACM* 2>/dev/null
groups
```
Record results in this handover. Then install PlatformIO if necessary, verify serial access, and use the official E1001 display example before composing the dashboard.

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

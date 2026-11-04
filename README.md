# EtherChat II

[![macOS](https://img.shields.io/badge/macOS-13%2B%20%C2%B7%20Apple%20Silicon-007AFF?logo=apple&logoColor=white)](https://github.com/N4EAC/EtherChat-II/releases/latest)

Amateur-radio chat for macOS with **modem73 and Xara bundled inside the app**. Select an engine in Station Settings; EtherChat II starts and stops it. No separate Xara application or modem installation is required.

## Download 1.2.3 - build 54

- [macOS Apple Silicon DMG](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.3/EtherChat-II-1.2.3-macOS-arm64.dmg)
- [User manual PDF](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.3/EtherChat-II-User-Manual.pdf)
- [Xara setup and validation guide](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.3/XARA_INTEGRATION.md)
- [Security and privacy review](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.3/SECURITY_REVIEW.md)
- [SHA-256 checksums](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.3/SHA256SUMS-1.2.3.txt)

Requires macOS 13 or later on Apple Silicon. The app is ad-hoc signed and is not notarized. Windows downloads are no longer distributed. This repository contains release information only; automatically generated source archives contain this README.

## Features

QST broadcast chat, channels/topics and user lists, direct conversations, CQ/SNR/73/custom macros, station beacons, Heard queries, saved contacts and favorites, an offline contact map, ADIF export for signing with TQSL, Default/CP/Crimson themes, and dockable modem activity.

Modem Activity follows the selected engine. Bundled Xara supplies live audio levels, signal/protocol measurements, counters, diagnostics and a compact waterfall. **Xara Instruments…** opens authenticated, read-only local panels. The bundled Xara engine is now **0.1.3**, with upstream SSID fixes and the revised buffering/resampling and TX latency model. Its unused ARQ data listener is disabled. Modem73 retains its own activity and CAT controls. Xara does not provide RF power/SWR/ALC or per-callsign SNR through this integration; measured F2/PING reports, RF meters and PSK Reporter uploads are unavailable with Xara. With bundled Xara and rigctld PTT, EtherChat II now reads frequency/mode directly and offers **Set Frequency** with PTT checks and radio readback confirmation. FlexRadio 6xxx uses a TCP CAT host:port instead of a serial device. Xara radio audio settings include **0 to +10 dB TX amplification**, saved and applied after restarting the modem.

## Start with Xara

1. Stop the modem and open **Station Settings → Modem engine → Xara**.
2. Leave **Run bundled Xara inside EtherChat II** enabled.
3. Refresh Xara audio devices and select the radio's USB input and output.
4. Choose HF 500/2300/2750 Hz or FM narrow/wide, then configure rigctld, serial RTS/DTR or VOX PTT. None is receive-only.
5. Save and press **Start Modem**. Stop before switching engines.

Both stations must use compatible modem waveforms. Xara and modem73 do not decode one another. Channel/direct features require a compatible application protocol. Chat packets are unacknowledged submissions.

Build 54 removes panel outlines, uppercase section headings, and the chat subtitle, and cleans obsolete source comments and asset-generation notes. Quit now performs asynchronous cleanup without blocking the UI; closing the last window also quits. App-owned helpers receive a bounded graceful stop with a forced-stop fallback, while external rigctld services remain untouched. Quit/last-window-close, helper cleanup, theme layouts, chat scrolling and CAT regressions passed.

Build 53 keeps **Set Frequency** stable while receiving: the button no longer flickers with receive/idle changes. Clicking while busy or disconnected gives an explanation; existing frequency-change safety checks remain.

Build 52 fixes CAT reading after switching from Xara to modem73. Bundled modem73 reads frequency, mode and supported meters automatically with rigctld PTT, even in older profiles with CAT saved as off. External modem73 retains its optional CAT setting. Mode-selection and simulated CAT read/tune/meter checks passed; physical-radio confirmation remains.

Build 51 fixes the Station Settings layout regression: the settings viewport stays bounded, long status messages cannot grow the page, and **Engine recovery…** opens a separate sheet. Render tests cover 1040×760 and 1300×900 in Default/CP/Crimson and recovery presentation. Update completion remains explicit: **Updated and selected automatically**. The selected version stays visible. Factory/previous-engine buttons are inside the separate **Engine recovery…** sheet; no second selection step follows an update. **Update modem73** handle audio recovery automatically. After Check Updates, it installs a verified gain-compatible engine, closes/reopens a running idle modem's saved radio devices and confirms the saved RX/TX gain. No zeroing gains or manual audio restart is needed. A stopped modem stays stopped. A failed install or audio restoration rolls back to the preceding engine and attempts to restore its audio.

The matching **modem73 2.5.0 EtherChat compatibility package** retains software gain, VUs, selected CoreAudio-device checks and control-safety patches. The updater retrieves it from this release after matching the upstream version and verifying its SHA-256 digest. It can also repair a previously installed stock 2.5.0 engine lacking gain support. Checks are operator-initiated and consult the upstream and EtherChat II GitHub releases; no station data, chat or audio is uploaded.

The automatic updater passed archive/URL/checksum/compatibility, reset/restart ordering and failure-recovery tests, including the live gain-compatible package download/install flow in an isolated store. Real RX/TX gain/drive/clipping, stream-reset gain retention, control telemetry and OFDM/ROBUST/MFSK DSP round trips passed without opening radio hardware. Previous build 47 passed targeted CAT readback/frequency-change/PTT-rejection and TX-gain configuration tests, plus app compilation, signature and disk-image verification. The unchanged bundled Xara workspace previously passed **466 tests**, with 8 hardware/capture-dependent tests skipped. macOS protocol/DSP and security regressions also passed. The bundled-library lifecycle and telemetry adapters were tested without RF. Physical radio audio, FT-710 device conversion, PTT and on-air interoperability remain to be verified by operators. Existing local settings and contacts are preserved. The sidebar title fits on one line, without a logo or powered-by banner.

## Security and privacy

The review found no evidence of covert developer uploads in the reviewed application paths. Required modem listeners bind to loopback; command/KISS/CAT ports still trust other local programs. Temporary maps and session files have restricted permissions, browser instrument controls are disabled, and installed-engine package integrity checks include companion files.

Station Settings discloses local storage and optional Internet requests. PSK Reporter is opt-in; update checks require a click; clicked message-link checks send the hostname to Cloudflare and Quad9. Radio packets, including direct conversations, are unencrypted. This review is not a malware-free guarantee or independent security certification; read the included security review for scope and limitations.

The bundled Xara macOS port is [N4EAC/xara-for-macos](https://github.com/N4EAC/xara-for-macos), based on [x0rro/xara](https://github.com/x0rro/xara). [modem73 source](https://github.com/RFnexus/modem73). Third-party notices are included in the application.

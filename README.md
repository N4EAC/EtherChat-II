# EtherChat II

[![macOS](https://img.shields.io/badge/macOS-13%2B%20%C2%B7%20Apple%20Silicon-007AFF?logo=apple&logoColor=white)](https://github.com/N4EAC/EtherChat-II/releases/latest)

Amateur-radio chat for macOS with **modem73 and Xara bundled inside the app**. Select an engine in Station Settings; EtherChat II starts and stops it. No separate Xara application or modem installation is required.

## Download 1.2.1

- [macOS Apple Silicon DMG](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.1/EtherChat-II-1.2.1-macOS-arm64.dmg)
- [User manual PDF](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.1/EtherChat-II-User-Manual.pdf)
- [Xara setup and validation guide](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.1/XARA_INTEGRATION.md)
- [SHA-256 checksums](https://github.com/N4EAC/EtherChat-II/releases/download/v1.2.1/SHA256SUMS-1.2.1.txt)

Requires macOS 13 or later on Apple Silicon. The app is ad-hoc signed and is not notarized. Windows downloads are no longer distributed. This repository contains release information only; automatically generated source archives contain this README.

## Features

QST broadcast chat, channels/topics and user lists, direct conversations, CQ/SNR/73/custom macros, station beacons, Heard queries, saved contacts and favorites, an offline contact map, ADIF export for signing with TQSL, Default/CP/Crimson themes, and dockable modem activity.

Modem Activity follows the selected engine. Bundled Xara supplies live audio levels, signal/protocol measurements, counters, diagnostics and a compact waterfall. **Xara Instruments…** opens its detailed local panels. Modem73 retains its own activity and CAT controls. Xara does not provide RF power/SWR/ALC or per-callsign SNR through this integration; measured F2/PING reports, CAT frequency/meters and PSK Reporter uploads are unavailable with Xara.

## Start with Xara

1. Stop the modem and open **Station Settings → Modem engine → Xara**.
2. Leave **Run bundled Xara inside EtherChat II** enabled.
3. Refresh Xara audio devices and select the radio's USB input and output.
4. Choose HF 500/2300/2750 Hz or FM narrow/wide, then configure rigctld, serial RTS/DTR or VOX PTT. None is receive-only.
5. Save and press **Start Modem**. Stop before switching engines.

Both stations must use compatible modem waveforms. Xara and modem73 do not decode one another. Channel/direct features require a compatible application protocol. Chat packets are unacknowledged submissions.

Protocol/DSP regression tests and the macOS port's 84 host/UI/engine/telemetry tests passed. The bundled-library lifecycle and telemetry adapters were tested without RF. Physical radio audio, FT-710 device conversion, PTT and on-air interoperability remain to be verified by operators. Existing local settings and contacts are preserved during the rename.

The bundled Xara macOS port is [N4EAC/xara-for-macos](https://github.com/N4EAC/xara-for-macos), based on [x0rro/xara](https://github.com/x0rro/xara). [modem73 source](https://github.com/RFnexus/modem73). Third-party notices are included in the application.

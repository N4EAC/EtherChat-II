# QSO73

[![macOS](https://img.shields.io/badge/macOS-13%2B%20%C2%B7%20Apple%20Silicon-007AFF?logo=apple&logoColor=white)](https://github.com/N4EAC/QSO73/releases/tag/v1.1.1)
[![Windows](https://img.shields.io/badge/Windows-10%2F11%20x64%20%C2%B7%20TESTING-orange)](https://github.com/N4EAC/QSO73/releases/tag/v1.1.1)

QSO73 is an amateur-radio chat client powered by modem73. It supports broadcast chat, channels and topics, direct conversations, station beacons, PING/SNR replies, Heard queries, optional PSK Reporter reception reporting, saved contacts and favorites, an offline contact map, and ADIF contact export.

This repository contains release information. Download the application packages below; GitHub's automatically generated source archives contain only this README.

## Standard release: 1.1.1

| Platform | Download | Status |
| --- | --- | --- |
| macOS 13+, Apple Silicon | [QSO73 1.1.1 DMG](https://github.com/N4EAC/QSO73/releases/download/v1.1.1/QSO73-1.1.1-macOS-arm64.dmg) | Development build, ad-hoc signed |
| Windows 10 (1903+) / Windows 11, x64 | [QSO73 1.1.1 portable ZIP](https://github.com/N4EAC/QSO73/releases/download/v1.1.1/QSO73-1.1.1-windows-x64-portable.zip) | **Testing** |

[Release notes](https://github.com/N4EAC/QSO73/releases/tag/v1.1.1) · [User manual PDF](https://github.com/N4EAC/QSO73/releases/download/v1.1.1/QSO73-User-Manual.pdf) · [SHA-256 checksums](https://github.com/N4EAC/QSO73/releases/download/v1.1.1/SHA256SUMS-1.1.1.txt)

macOS builds are for Apple Silicon and are not notarized. Windows builds are unsigned and remain testing builds. On Windows, extract the entire portable folder to a writable location and keep the engine and hamlib folders beside QSO73.exe. No separate Hamlib installation or PATH change is needed.

Preserve your settings and personal records when updating. Windows stores settings.json, contacts.json and station-directory.json beside QSO73.exe. These files are not included in the distributed ZIPs.

## Windows Diagnostic 1

For CAT/PTT troubleshooting, use the separate **[Windows Diagnostic 1 portable ZIP](https://github.com/N4EAC/QSO73/releases/download/v1.1.1-windows-diagnostic1/QSO73-1.1.1-windows-x64-diagnostic1-portable.zip)**. This testing build does not replace the standard release.

[Diagnostic release notes and instructions](https://github.com/N4EAC/QSO73/releases/tag/v1.1.1-windows-diagnostic1) · [Diagnostic SHA-256 checksum](https://github.com/N4EAC/QSO73/releases/download/v1.1.1-windows-diagnostic1/SHA256SUMS-Windows-Diagnostic1.txt)

1. Extract it into its own writable folder, close other QSO73 instances, and run QSO73.exe. The window title identifies **Windows DIAGNOSTIC 1**.
2. Configure the radio audio and CAT/PTT route, then reproduce the issue. The chat window displays the engine-reported transmit mode above the audio meters.
3. Close QSO73 normally if possible. Send **QSO73-debug-report.txt** from the Desktop folder named **QSO73-Debug-...**. If crash.txt contains text, include it too. Alternatively, compress and send the entire folder.

**Setup -> Open Desktop Debug Folder** opens the current report folder. Reports are created automatically, including failed modem startup attempts, and contain detailed engine/Hamlib logs, selected settings, COM mappings and connection errors. Nothing is uploaded automatically. Reports can contain callsigns, grids, radio messages and network addresses; review before sharing. If Windows cannot write to the Desktop, a message identifies a fallback folder beside the application.

Detailed instructions and the bundled modem73 CAT/PTT interface review are included in the diagnostic ZIP. Windows hardware verification, including IC-7760/Win4IcomSuite/com0com/CAT7200, remains pending.

## Radio setup

Select explicit radio audio input and output devices. Choose the modem family/mode and the appropriate PTT method. The modem processes 48 kHz internally and converts supported hardware rates, including 44.1 kHz USB audio devices.

- **Direct serial CAT:** use rigctl PTT, automatic Hamlib/rigctld, your actual radio model, its serial port and matching baud. For a direct FT-710 connection, the radio model is **1049**. **2 - Hamlib NET rigctl** is a network backend, not a physical-radio model.
- **Existing rigctld:** configure its host and port. QSO73 reuses the service and leaves it running on Stop.
- **FLRig:** use automatic Hamlib with model **4** and FLRig's XML-RPC endpoint, commonly 127.0.0.1:12345. QSO73's local rigctld listening port must be different, normally 4532.
- **CAT-free PTT:** use Serial DTR/RTS on macOS or **com** on Windows, with the working port and RTS/DTR line. VOX and none are also available. These CAT-free choices do not provide CAT frequency readback or PSK Reporter uploads.

Both stations need compatible modem settings and matching RF/audio configuration. Channels and direct conversations share radio airtime, have no delivery acknowledgment, and are readable over the air. F1-F4 submit immediately; beacons and automatic replies also use radio airtime.

See the **25-page user manual** for operating instructions, modem modes, channels, private conversations, contact logging and connection examples. CAT, FLRig, virtual ports and serial-only PTT are covered on page 25.

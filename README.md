# QSO73

[![macOS](https://img.shields.io/badge/macOS-13%2B%20%C2%B7%20Apple%20Silicon-007AFF?logo=apple&logoColor=white)](https://github.com/N4EAC/QSO73/releases/tag/v1.2.0)
[![Windows](https://img.shields.io/badge/Windows-10%2F11%20x64%20%C2%B7%20TESTING-orange)](https://github.com/N4EAC/QSO73/releases/tag/v1.2.0)

QSO73 is an amateur-radio chat client with modem73 and an optional external Xara backend. It supports broadcast chat, channels and topics, direct conversations, station beacons, PING/SNR replies, Heard queries, optional PSK Reporter reception reporting, saved contacts and favorites, an offline contact map, and ADIF contact export.

This repository contains release information. Download the application packages below; GitHub's automatically generated source archives contain only this README.

## Standard release: 1.2.0

| Platform | Download | Status |
| --- | --- | --- |
| macOS 13+, Apple Silicon | [QSO73 1.2.0 DMG](https://github.com/N4EAC/QSO73/releases/download/v1.2.0/QSO73-1.2.0-macOS-arm64.dmg) | Development build, ad-hoc signed |
| Windows 10 (1903+) / Windows 11, x64 | [QSO73 1.2.0 portable ZIP](https://github.com/N4EAC/QSO73/releases/download/v1.2.0/QSO73-1.2.0-windows-x64-portable.zip) | **Testing** |

[Release notes](https://github.com/N4EAC/QSO73/releases/tag/v1.2.0) · [User manual PDF](https://github.com/N4EAC/QSO73/releases/download/v1.2.0/QSO73-User-Manual.pdf) · [SHA-256 checksums](https://github.com/N4EAC/QSO73/releases/download/v1.2.0/SHA256SUMS-1.2.0.txt)

macOS builds are for Apple Silicon and are not notarized. Windows builds are unsigned and remain testing builds. On Windows, extract the entire portable folder to a writable location and keep the engine and hamlib folders beside QSO73.exe. No separate Hamlib installation or PATH change is needed.

Preserve your settings and personal records when updating. Windows stores settings.json, contacts.json and station-directory.json beside QSO73.exe. These files are not included in the distributed ZIPs.

## Choose modem73 or Xara

Version **1.2.0** adds a modem selector in macOS **Station Settings -> Modem engine** and Windows **Setup -> Modem**. Existing settings continue using modem73; its local audio/PTT/mode configuration is preserved when switching.

**Xara is an external-host option.** Run and configure Xara on its Linux host first, then enter the host, **command port 8300** and **KISS port 8100** in QSO73. Port 8301 is ARQ data and is not used. This release does not bundle a native Mac/Windows Xara executable. Configure Xara's audio, waveform and PTT there; use a trusted network or your existing tunnel.

Packet Radio Chat, QSO73 channels/topics/direct envelopes, CQ/73/custom messages, beacons and Heard queries use Xara's AX.25 KISS interface. Both stations need compatible Xara waveforms; Xara and modem73 are not interchangeable over the air. This does not add ARQ sessions or compatibility with another application's chat protocol.

Xara host readiness/busy/PTT/queue information is shown, with local KISS packet counts. Audio VUs, decoding indication, CAT controls, measured per-station SNR/F2/PING reports and PSK Reporter uploads are unavailable with this interface. A host SNR is not assigned to a callsign or packet. Real Xara/Linux DSP and on-air testing remain pending; protocol/state fixtures and the client builds pass.

Read the [Xara setup guide](https://github.com/N4EAC/QSO73/releases/download/v1.2.0/XARA_INTEGRATION.md) and page **26** of the updated manual. The guide is also included in both application packages.

## Windows Diagnostic 1

This retained diagnostic build is based on 1.1.1 for modem73/CAT testing; it does not include the new Xara selector.

For CAT/PTT troubleshooting, use the separate **[Windows Diagnostic 1 portable ZIP](https://github.com/N4EAC/QSO73/releases/download/v1.1.1-windows-diagnostic1/QSO73-1.1.1-windows-x64-diagnostic1-portable.zip)**. This testing build does not replace the standard release.

[Diagnostic release notes and instructions](https://github.com/N4EAC/QSO73/releases/tag/v1.1.1-windows-diagnostic1) · [Diagnostic SHA-256 checksum](https://github.com/N4EAC/QSO73/releases/download/v1.1.1-windows-diagnostic1/SHA256SUMS-Windows-Diagnostic1.txt)

1. Extract it into its own writable folder, close other QSO73 instances, and run QSO73.exe. The window title identifies **Windows DIAGNOSTIC 1**.
2. Configure the radio audio and CAT/PTT route, then reproduce the issue. The chat window displays the engine-reported transmit mode above the audio meters.
3. Close QSO73 normally if possible. Send **QSO73-debug-report.txt** from the Desktop folder named **QSO73-Debug-...**. If crash.txt contains text, include it too. Alternatively, compress and send the entire folder.

**Setup -> Open Desktop Debug Folder** opens the current report folder. Reports are created automatically, including failed modem startup attempts, and contain detailed engine/Hamlib logs, selected settings, COM mappings and connection errors. Nothing is uploaded automatically. Reports can contain callsigns, grids, radio messages and network addresses; review before sharing. If Windows cannot write to the Desktop, a message identifies a fallback folder beside the application.

Detailed instructions and the bundled modem73 CAT/PTT interface review are included in the diagnostic ZIP. Windows hardware verification, including IC-7760/Win4IcomSuite/com0com/CAT7200, remains pending.

## Radio setup

The CAT/PTT choices below apply to modem73. Configure Xara radio audio, waveform and PTT on its external host.

Select explicit radio audio input and output devices. Choose the modem family/mode and the appropriate PTT method. The modem processes 48 kHz internally and converts supported hardware rates, including 44.1 kHz USB audio devices.

- **Direct serial CAT:** use rigctl PTT, automatic Hamlib/rigctld, your actual radio model, its serial port and matching baud. For a direct FT-710 connection, the radio model is **1049**. **2 - Hamlib NET rigctl** is a network backend, not a physical-radio model.
- **Existing rigctld:** configure its host and port. QSO73 reuses the service and leaves it running on Stop.
- **FLRig:** use automatic Hamlib with model **4** and FLRig's XML-RPC endpoint, commonly 127.0.0.1:12345. QSO73's local rigctld listening port must be different, normally 4532.
- **CAT-free PTT:** use Serial DTR/RTS on macOS or **com** on Windows, with the working port and RTS/DTR line. VOX and none are also available. These CAT-free choices do not provide CAT frequency readback or PSK Reporter uploads.

Both stations need compatible modem settings and matching RF/audio configuration. Channels and direct conversations share radio airtime, have no delivery acknowledgment, and are readable over the air. F1-F4 submit immediately; beacons and automatic replies also use radio airtime.

See the **26-page user manual** for operating instructions, modem modes, channels, private conversations, contact logging and connection examples. CAT, FLRig, virtual ports and serial-only PTT are covered on page 25.

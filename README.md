# JS8Call-Mobile

**JS8Call-Mobile** is an amateur radio weak-signal digital mode client for iPadOS, built on the **JS8Core** engine. It allows licensed amateur radio operators to decode and transmit JS8 messages over a local network **TCI (Transceiver Control Interface)** connection or via direct iPad audio coupling.

* **Author:** Chris Olson (AC9KH)
* **License:** BSD 3-Clause (App) / MIT (JS8Core)
* **Privacy Policy:** [View Privacy Policy](PRIVACY.md)
* **Support & Bug Reports:** [GitHub Issues](https://github.com/Chris-AC9KH/JS8Call-Mobile/issues)

---

## Features

* **TCI Network Integration:** Connects directly over Wi-Fi/LAN to TCI-compatible Software Defined Radios (SDRs) and transceiver servers (such as ExpertSDR / Thetis / SunSDR) for real-time VFO frequency readout, IQ/audio streaming, and PTT keying.
* **Local iPad Audio Mode:** Decode and transmit JS8 signals using your iPad's built-in microphone/speaker or an external USB/lightning audio interface when TCI is disconnected.
* **Live Waterfall & Passband Monitor:** Real-time spectrum waterfall (`500–3000 Hz`) with adjustable **Zero** floor, **Range**, **Flatten baseline** toggle, and visual TX audio offset marker.
* **Multi-Frame Message Assembly:** Automatically assembles multi-frame JS8 transmissions in place with UTC timestamps, audio offset (`Hz`), signal-to-noise ratio (`SNR`), callsign, and frame status indicators (`[incomplete]`, `[checksum failed]`).
* **Automated Station Replies:** Supports automatic Heartbeat acknowledgments (`@HB`) and directed station queries (`SNR?`, `GRID?`, `INFO?`, `STATUS?`, `MSG`).

---

## Quick Start Guide

### 1. Configure Your Station Identity
1. Tap the **Gear icon** (`⚙️`) in the top-right corner of the **Control Console** to open **Preferences and Settings**.
2. Enter your **Station Callsign** (e.g., `AC9KH`) and **Grid Square** (4 or 6 characters, e.g., `EN45`).
3. Tap **Done** to save. Your settings are stored locally on your iPad.

### 2. Choose Your Audio / Radio Connection
JS8Call-Mobile supports two operating modes:

* **Option A: TCI Network Connection (Recommended)**
  1. Open **Preferences and Settings** and enter your TCI server's **IP Address** (or `.local` hostname) and **Connection Port** (default `40001` or `50001`).
  2. Ensure **Use iPad audio when TCI is disconnected** is turned off (or leave it on as a fallback).
  3. On the main **Control Console**, tap **Connect TCI**. The status dot will turn green (**Connected**) and your active VFO frequency will appear at the top.

* **Option B: Local iPad Audio Coupling**
  1. Open **Preferences and Settings** and enable **Use iPad audio when TCI is disconnected**.
  2. Grant microphone permission when prompted by iPadOS.
  3. Use a USB audio interface connected to your transceiver or acoustic coupling near your radio's speaker/mic.

---

## Control Console & Operating Guide

* **Frequency Readout:** Displays the active VFO frequency reported by your TCI server in MHz.
* **Connect TCI / Disconnect:** Opens or closes the network socket to your TCI server. A red **TX** badge appears next to the status indicator whenever the transmitter is keyed.
* **TUNE:** Transmits a continuous carrier tone at your selected **Audio Offset** frequency so you can tune an antenna tuner or verify RF output. Tap **TUNING...** again to stop. *(Requires active TCI connection.)*
* **SEND HEARTBEAT:** Broadcasts an `@HB HEARTBEAT [GRID]` frame on a clear frequency automatically chosen inside the `500–950 Hz` heartbeat sub-band.
* **Audio Offset (500–3000 Hz):** Sets your transmit audio tone frequency in 10 Hz steps, indicated by the vertical marker on the waterfall.
* **Waterfall Controls:**
  * **Zero:** Adjusts the minimum signal floor (`dB`) displayed on the waterfall.
  * **Range:** Adjusts the dynamic contrast range (`dB`) of incoming signals.
  * **Flatten baseline:** Normalizes passband tilt across the receiver filter width.

---

## Sending & Reading Messages

* **Live Message Log:** Displays decoded messages chronologically from top to bottom.
  * **Green-tinted rows** indicate messages addressed directly to your callsign.
  * **Red text / red-tinted rows** indicate your own outgoing transmissions (`TX`).
  * **Orange text** indicates partial (`[incomplete]`) or corrupted (`[checksum failed]`) frames.
* **Follow / Clear:** **Follow** keeps the log scrolled to the newest incoming message (touching/scrolling the log manually pauses Follow until toggled back on). **Clear** empties the current session log.
* **Transmitting a Message:** Type your message in the bottom bar (for example, `W1AW SNR?` or `CQ CQ CQ`) and tap **TX Send**. Your station callsign prefix is added automatically. Note that unlike the desktop version of JS8Call, you must type the destination callsign or group callsign and use proper JS8 spec formatting for your transmitted message. Example; to query for SNR you would type `W1AW SNR?` JS8Call-Mobile will not fill in the destination callsign for you automatically.

---

## Auto-Reply & Heartbeat Networking

Open **Preferences and Settings** to configure unattended or semi-automated station responses:

* **Enable Auto-Replies (AUTO):** When enabled, JS8Call-Mobile automatically responds to directed commands addressed to your callsign:
  * `[YOURCALL] SNR?` → Replies with the sender's signal report (`SNR +XX`).
  * `[YOURCALL] GRID?` → Replies with your configured Maidenhead grid square.
  * `[YOURCALL] INFO?` → Replies with your custom **INFO? Response Msg**.
  * `[YOURCALL] STATUS?` → Replies with your custom **STATUS? Response Msg**.
  * `[YOURCALL] MSG ...` → Replies with `ACK` confirming message receipt.
* **Enable Heartbeat ACK:** Automatically responds to incoming `@HB` broadcasts with a signal report (`HEARTBEAT SNR +XX`) on an open sub-band offset. Includes a built-in **55-minute cooldown** per callsign to prevent duplicate QRM.
* **Hold PTT between frames of multi-frame messages:** Keeps the transmitter keyed continuously across frame boundaries during multi-frame transmissions instead of unkeying between frames.

At present this is a partially supported subset of the JS8 directed commands. As JS8Call-Mobile is developed further, new capabilities will be added.

---

## URLs for App Store Connect & Settings

* **User Manual URL**: (this document)
* **Support URL**: Issues list at: [https://github.com/Chris-AC9KH/JS8Call-Mobile/issues](https://github.com/Chris-AC9KH/JS8Call-Mobile/issues)
* **Privacy Policy URL:** [https://github.com/Chris-AC9KH/JS8Call-Mobile/blob/main/PRIVACY.md](https://github.com/Chris-AC9KH/JS8Call-Mobile/blob/main/PRIVACY.md)

---

## Acknowledgments & Licenses

* **JS8Call-Mobile** is licensed under the **BSD 3-Clause License**. See [`LICENSE`](LICENSE) for full details.
* Built using **[JS8Core](https://github.com/JS8Call-improved/JS8Core)**, licensed under the **MIT License** (Copyright © 2025 js8core contributors, © 2018 Jordan Sherer, © 2026 JS8Call Official).

# JS8Call-Mobile

*Coming soon to the Apple App Store for iPadOS and Mac*

**User and Quick-Start Guide:**

**JS8Call-Mobile** is a full-featured amateur radio weak-signal digital mode client for iPadOS (also runs on Mac), built on the **JS8Core** engine. It allows licensed amateur radio operators to decode, compose, relay, and store-and-forward JS8 messages over a local network **TCI (Transceiver Control Interface)** connection or via direct iPad audio coupling.

* **Developer:** Chris Olson (AC9KH)
* **License:** BSD 3-Clause (App) / MIT (JS8Core)
* **Privacy Policy:** [View Privacy Policy](PRIVACY.md)
* **Support & Bug Reports:** [GitHub Issues](https://github.com/Chris-AC9KH/JS8Call-Mobile/issues)

---

## Features

* **TCI Network Integration:** Connects directly over Wi-Fi/LAN to any TCI-compatible SDR server or client—including native TCI platforms (such as **ExpertSDR3**, **Thetis**, **SunSDR**, **AetherSDR**, **Quisk**, and **TCIBridge**) as well as Marcus Roskosch's (DL8MRE) **Common-Radio** apps for macOS/iPadOS—providing real-time VFO tuning, band preset switching, audio streaming, and PTT keying across a wide range of transceivers.

### Supported TCI Servers, Clients & Radios

| TCI Server / SDR Client | Platform | Supported Transceivers & Hardware |
| :--- | :--- | :--- |
| **ExpertSDR3 / ExpertSDR2** | Windows, macOS, Linux | Expert Electronics SunSDR2 DX, SunSDR2 PRO, SunSDR2 QRP, MB1, ColibriDDC |
| **Thetis** | Windows | Apache Labs ANAN series (OpenHPSDR protocol radios) and Hermes-Lite 2 |
| **AetherSDR** | macOS, Linux | FlexRadio FLEX-6000 and FLEX-8000 Signature Series |
| **Quisk** *(N2ADR)* | Windows, Linux, macOS | Hermes-Lite 2, HiQSDR, Odyssey, SoftRock, SDR-IQ, Perseus, and SoapySDR hardware |
| **TCIBridge** *(AC9KH)* | macOS, Linux | Supports over 240 radios and more than 200 overall across hardware transceivers, receivers, SDRs, and virtual rig interfaces |
| **SmartSDR for Mac / iOS** *(DL8MRE)* | macOS, iPadOS, iOS | FlexRadio FLEX-6000, FLEX-8000, and Aurora Series (local or SmartLink) |
| **SDR-Control** *(DL8MRE)* | macOS, iPadOS, iOS | Icom IC-705, IC-7300, IC-7300 MK2, IC-7610, IC-7760, IC-9700, IC-R8600 |
| **FT-Control** *(DL8MRE)* | macOS, iPadOS, iOS | Yaesu FTdx101D, FTdx101MP, FTdx10, FT-710 *(via Yaesu SCU-LAN10)* |
| **TS-Control** *(DL8MRE)* | macOS, iPadOS, iOS | Kenwood TS-890S *(via built-in LAN)* |
| **K4-Control** *(DL8MRE)* | macOS, iPadOS, iOS | Elecraft K4, K4D, K4HD |

* **Local iPad Audio Mode:** Decode and transmit JS8 signals using your iPad's built-in microphone/speaker
* **Using Non-TCI Transceivers:** Any radio with analog audio I/O (such as the Xiegu G90, older HF transceivers, or field QRP rigs) can still be used with JS8Call-Mobile in **Local iPad Audio Mode**. Simply connect a class-compliant USB sound card or USB-C audio interface (such as a Digirig or Sabrent USB audio adapter) to your iPad and enable **VOX** on your transceiver for PTT keying.
* **Split Band & Call Activity and Directed Messages Panes:** Separates general band monitoring (**Band & Call Activity**) from directed messages, joined `@GROUP` traffic, `@ALLCALL` broadcasts, and your own transmissions (**Directed Messages**).
* **Tap-to-Target QSOs & Command Helper:** Tap any incoming row in **Directed Messages** or **Band & Call Activity **to lock onto that station for a multi-turn QSO, or tap-and-hold (right-click on Mac) to open a categorized JS8 command helper menu.
* **Multi-Frame Assembly & Speed Modes:** Automatically assembles multi-frame JS8 transmissions in place with UTC timestamps, audio offset (`Hz`), signal-to-noise ratio (`SNR`), callsign, submode (`S`, `N`, `F`, `40`, `60`), and frame status indicators (`[incomplete]`, `[checksum failed]`). **NOTE:** JS8Call-Mobile only supports transmitting in Slow, Normal or Fast modes since VOX won't work reliably with JS8 40 and JS8 60 modes due to clipping of leading symbols when using a VOX trigger to key your rig. This is a design choice in JS8Call-Mobile since these modes are not used very often.
* **Store-and-Forward Inbox & Live Relays:** Full support for storing messages in a local inbox, multi-hop relay routing (`>`), automatic `RETRIEVE MSG` notifications, and full JS8 directed command auto-replies.
* **Live Waterfall & Passband Monitor:** Real-time spectrum waterfall (`0–3000 Hz`) with adjustable **Zero** floor, **Range**, **Flatten baseline** toggle, and visual TX audio offset marker.
* **Saves Logs:** Band & Call Activity and Directed Messages logs are saved for each band, persistent on app shutdown and restart, until they are cleared using the **Clear Band/Call Log** buttons. Will store up to 400 records for each log, for each band. A numerical indicator at the right of each log header shows the number of records stored in the database for that band.
* **Screen-Off Background Monitoring:** JS8Call-Mobile continues to run normally when you lock the iPad screen to conserve battery power during extended uptime. Automatically pauses speaker audio during incoming phone calls and resumes when the call ends.
* **Group Callsigns (`@GROUP`):** Join one or more custom groups (such as `@EMCOMM`, `@ARES`, `@RACES`) to monitor group traffic in **Directed Messages**, store group `MSG` broadcasts in your Inbox, and answer directed group queries.

---

## Quick Start Guide

### 1. Configure Your Station Identity & Groups
1. Tap the **Gear icon** (`⚙️`) in the top-right corner of the **Controls** to open **Preferences and Settings**.
2. Enter your **Station Callsign** (e.g., `AC9KH`) and **Grid Square** (4 or 6 characters, e.g., `EN45`).
3. *(Optional)* Enter a comma-separated list of **Group Callsigns** you want to monitor (e.g., `@EMCOMM, @ARES`).
4. Tap **Done** to save. Your settings are stored locally on your iPad.

### 2. Choose Your Audio / Radio Connection
JS8Call-Mobile supports three operating modes:

* **Option A: TCI Network Connection (recommended)**
  1. Open **Preferences and Settings** and enter your TCI server's **IP Address** (or `.local` hostname) and **Connection Port** (default **`40001`** for most TCI clients including DL8MRE Common-Radio apps, or `50001` on some ExpertSDR/Thetis/AetherSDR and TCIBridge setups).
  2. Ensure **Use iPad audio when TCI is disconnected** is turned off. Only use this if you intend to use USB or mic/speaker audio.
  3. By default, live TCI receive audio plays through the iPad's speaker so you can monitor band audio directly. To silence the iPad speaker during long unattended or screen-off monitoring sessions while keeping the TCI connection active, enable **Mute iPad audio when TCI is connected** in **Preferences and Settings**.
  4. On the main **Controls**, tap **Connect TCI**. The status dot will turn green (**Connected**) and your active VFO frequency will appear at the top. You can now press the iPad's power button to turn off the display and save battery while JS8Call-Mobile continues decoding and handling traffic in the background.

### Using TCIBridge (Companion App by Chris AC9KH)
**[TCIBridge](https://github.com/Chris-AC9KH/TCIBridge)** is a free, open-source TCI Bridge developed by Chris AC9KH specifically for **JS8Call-Mobile**. It turns a Mac or Linux computer (such as a headless Raspberry Pi 4b/5 in your shack) into a **TCI 2.1** network server for over 240 Hamlib-supported transceivers using standard USB CAT and USB audio interfaces.

1. **Install & Launch TCIBridge:**
   * **macOS:** Download the prebuilt `.dmg` from the [TCIBridge Releases](https://github.com/Chris-AC9KH/TCIBridge/releases/tag/v1.0.1) and run it.
   * **Linux / Raspberry Pi (`arm64`):** Install the `.deb` package from [TCIBridge Releases](https://github.com/Chris-AC9KH/TCIBridge/releases/tag/v1.0.1) (`sudo apt install ./tcibridge_*_arm64.deb`) to run TCIBridge automatically as a background `systemd` service on a Raspberry Pi4b or Pi5 TCI Server in your shack.
2. **Configure Rig & Audio:** Open `http://localhost:58080` if running on your Mac. If running on a Pi TCI server open `http://<server_IP_address:58080` in your web browser on any LAN computer or iPad. On iPad tap **Configure the Companion TCIBridge Radio Connection** in JS8Call-Mobile's Preferences. Select your transceiver model, serial port, baud rate, PTT method, and USB audio device. Click or tap the `Save & Apply Settings` button at the bottom.
3. **Connect from JS8Call-Mobile:** In **Preferences and Settings** JS8Call-Mobile will automatically detect a running TCIBridge server, pick your discovered **TCI Bridge** server from the list (or enter its IP address with port **`50001`** manually), and tap **Connect TCI** on the main interface.

 **Option B: USB Audio Connection**
  1. Open **Preferences and Settings** and enable **Use iPad audio when TCI is disconnected**.
  2. Grant microphone permission when prompted by iPadOS.
  3. Use a USB-C or Lightning to analog audio interface connected to your iPad.

* **Option C: Local iPad Audio Coupling**
  1. Open **Preferences and Settings** and enable **Use iPad audio when TCI is disconnected**.
  2. Grant microphone permission when prompted by iPadOS.
  3. Use acoustic coupling near your radio's speaker/mic.

---

## Controls & Operating Guide

* **Frequency Readout & Band Selector:** Displays the active VFO frequency in `kHz` (e.g., `14,078 kHz`). Tap the frequency readout while connected to TCI to switch directly to standard JS8 dial frequencies across `160m` through `2m`.
* **Inbox (`📥`):** Opens your stored message inbox. A red badge displays the count of unread messages addressed to your callsign. You can compose outbound store-and-forward messages, read received messages, and manage stored traffic.
* **Connect TCI / Disconnect:** Opens or closes the network socket to your TCI server. A red **TX** badge appears next to the status indicator whenever the transmitter is keyed.
* **TUNE:** Transmits a continuous carrier tone at your selected **Audio Offset** frequency so you can tune an antenna tuner or verify RF output. Tap **TUNING...** again to stop *(requires active TCI connection, tune is disabled for iPad audio)*.
* **SEND HEARTBEAT:** Broadcasts an `@HB HEARTBEAT [GRID]` frame on a clear frequency automatically chosen inside the `500–1000 Hz` heartbeat sub-band.
* **TX Mode Speed:** Selects your outbound transmit submode: **Slow (30s)**, **Normal (15s)**, or **Fast (10s)**. Incoming frames are decoded across all supported submodes (`S`, `N`, `F`, `40`, `60`).
* **Audio Offset (500–3000 Hz):** Sets your transmit audio tone frequency in 10 Hz steps, indicated by the vertical marker on the waterfall. Your offset remains locked where you set it for all directed transmissions and replies; only `@HB` broadcasts and `HEARTBEAT ACK` responses use the `500–1000 Hz` heartbeat sub-band.
* **Waterfall Controls:**
  * **Zero:** Adjusts the minimum signal floor (`dB`) to remove "white noise" from the waterfall.
  * **Range:** Adjusts the dynamic contrast range (`dB`) of incoming signals.
  * **Flatten baseline:** Normalizes passband tilt across the receiver filter width.
  * **Abort Transmission** A Tx timer indicator will appear on the waterfall indicating wait time until Tx begins, and total remaining time to the end of the last frame once Tx starts. Tap or click the indicator to abort your transmission if desired.

## TX Drive & Audio Gain Calibration

iPad's can tend to produce TCI audio that is very "hot". JS8Call-Mobile includes a logarithmic **TX Drive** attenuator (`-45.0 dB` to `0.0 dB`) in the Left Control Console. Proper TX Drive ensures a clean, narrow FSK/GFSK waveform without digital clipping, ALC overshoot, or passband splatter.

### Why Gain Staging Matters
Digital mode transmissions require a completely linear audio path from the iPad to the transceiver's modulator. If the incoming TCI audio stream exceeds `0 dBFS` or overdrives the radio's audio input, the rig's ALC circuit clamps down on the signal, creating wide harmonic spurs and horizontal flashes across the passband.

### Step-by-Step Calibration (Zero ALC Method)
1. **Select Data Mode:** Set your transceiver to **USB-D** (USB Data) with a **3.0 kHz (WIDE)** TX filter so voice processing, compression, and microphone equalizers are bypassed.
2. **Set a Safe Hardware Power Ceiling:** Set your transceiver's **RF Power** control to your desired maximum operating power (for example, **7%–25%** on a 100W rig for QRP/low-power operation). Avoid leaving RF Power at 100% while throttling audio down to a few watts, as any stray audio transient could momentarily transmit at full power.
3. **Set Radio USB Audio Input:** Set your radio's USB modulation level (such as `USB MOD Level` on Icom transceivers) to a moderate mid-low range, typically **25%–40%**.
4. **Start Low on TX Drive:** In JS8Call-Mobile's Controls, start with the **TX Drive** slider around **-20.0 dB**.
5. **Key a Test Carrier:** Tap **TUNE** in JS8Call-Mobile (preferably into a dummy load or on a clear frequency) while watching your radio's **ALC** and **Po (Power)** meters.
6. **Dial In Output Power:** Slowly raise the **TX Drive** slider until your wattmeter reaches your target output power while the **ALC meter shows zero bars** (or barely flickers at the very bottom edge of the scale).
7. **Stop Tuning:** Tap **TUNING...** again to release PTT. Your calibrated **TX Drive** level is saved automatically.

---

## Reading & Composing Messages

### Split Activity Logs
The main log view is divided into two synchronized panes sharing the same columns (`UTC`, `Hz`, `SNR`, `Callsign`, `Mode`, `Message`):

* **Band & Call Activity (Top Pane):** Displays all decoded incoming traffic on the band.
  * **Green-tinted rows** highlight messages addressed directly to your callsign, your joined `@GROUP` callsigns, or relayed through your station.
  * **Orange text** indicates partial (`[incomplete]`) or corrupted (`[checksum failed]`) frames.
* **Directed Messages (Middle Pane):** Filters traffic down to QSO-relevant activity: incoming messages addressed to you, joined `@GROUP` traffic, `@ALLCALL` traffic, and your own outgoing transmissions.
  * **Red text** indicates your own outgoing transmissions (`TX`).
  * **NOTE:** JS8Call-Mobile does not display an EOT or End Of Transmission indicator. Incoming messages appear as greyed-out text followed by three dots `…` until the message is complete, at which time the text switches to normal, indicating EOT.
* **Follow / Clear Controls:**
  * **Follow** keeps both logs scrolled to the newest message (dragging either log manually pauses Follow until toggled back on).
  * **Clear Band Log** empties the top Band & Call Activity pane.
  * **Clear Call Log** empties the middle Directed Messages pane (and clears `AGN?` repeat history).

### Tap-to-Target & Command Helper
1. **Lock a Target Station:** Tap any incoming row in **Directed Messages** or **Band & Call Activity** to select that station. A blue `To: CALLSIGN ×` pill appears in the composition bar and stays locked across multi-turn exchanges until you tap **`×`**, tap the row again, or tap a different station.
2. **Long-Press Command Helper:** Tap and hold (or right-click on Mac) any incoming row in **Directed Messages** or **Band & Call Activity** to open a categorized menu of JS8 directed commands (`SNR?`, `GRID?`, `INFO?`, `STATUS?`, `HEARING?`, `AGN?`, `MSG`, `MSG TO:`, `>`, `QUERY CALL`, `QUERY MSGS`, `QUERY MSG`, plus quick `SNR` and `GRID` reports). Selecting a command locks the target callsign and populates the text entry box so you can review or append text before sending.
3. **Multi-Line Composition:** Type your message in the bottom bar and tap **TX Send** (or press **Return** on a hardware keyboard). The entry box expands vertically up to 5 lines as you type longer messages, and your station callsign prefix (`YOURCALL: `) is prepended automatically.

---

## Auto-Reply, Groups, Relays & Store-and-Forward Networking

Open **Preferences and Settings** to configure unattended or semi-automated station responses:

* **Enable Auto-Replies (AUTO):** When enabled, JS8Call-Mobile automatically responds to directed commands addressed to your callsign—or any joined `@GROUP` callsign—on your configured **Audio Offset**:
  * `[YOURCALL] SNR?` (or `[@GROUP] SNR?`) → Replies with the sender's signal report (`SNR +XX`).
  * `[YOURCALL] GRID?` (or `[@GROUP] GRID?`) → Replies with your configured Maidenhead grid square.
  * `[YOURCALL] INFO?` (or `[@GROUP] INFO?`) → Replies with your custom **INFO? Response Msg**.
  * `[YOURCALL] STATUS?` (or `[@GROUP] STATUS?`) → Replies with your custom **STATUS? Response Msg**.
  * `[YOURCALL] HEARING?` (or `[@GROUP] HEARING?`) → Replies with up to the 4 most recently heard callsigns (`HEARING CALL1 CALL2 CALL3 CALL4`).
  * `[YOURCALL] QUERY CALL [CALL]?` (or `[@GROUP] QUERY CALL [CALL]?`) → Replies with `YES [CALL] [SNR] [AGE]` if heard, or `NO` (for direct personal queries) if not heard.
  * `[YOURCALL] AGN?` → Re-transmits your most recent outgoing message to that station from **Directed Messages**.
  * `[YOURCALL] MSG [TEXT]` / `MSG TO:[CALL] [TEXT]` → Stores the message in your local Message Inbox and replies with `ACK`.
  * `[@GROUP] MSG [TEXT]` → Displays in **Directed Messages** and stores the message in your local Message Inbox (`To: @GROUP`) without transmitting an `ACK` so multiple group members do not collide on air.
  * `[YOURCALL] QUERY MSGS` / `QUERY MSG [ID]` → Advertises (`YES MSG ID #`) and delivers stored messages addressed to the requesting station, marking them read upon `ACK`.
  * `[YOURCALL]>[NEXTHOP] [TEXT]` → Automatically forwards multi-hop relay frames along the specified individual callsign path and routes returning `ACK` confirmations back to the originator.
* **`@ALLCALL` Broadcasts:** Incoming `@ALLCALL` messages are logged in **Directed Messages** for monitoring, but JS8Call-Mobile never transmits an automated reply to an `@ALLCALL` broadcast.
* **Push Retrieve Notices & Alerts:** When **Auto-Replies** is enabled, JS8Call-Mobile periodically notifies recently heard stations (`[CALL] RETRIEVE MSG [ID]`) if you are holding unread mail for them. When another station sends you a `RETRIEVE MSG` notice, an alert banner pops up with the exact `QUERY MSG` command needed to retrieve it. If JS8Call-Mobile has sent a stored message notification to a station and the message is not retrieved, it will re-notify at most once every 8 hours if that station is seen on the band again.
* **Enable Heartbeat ACK:** Automatically responds to incoming `@HB` broadcasts with a signal report (`HEARTBEAT SNR +XX`) on a clear `500–1000 Hz` sub-band offset. JS8Call-Mobile will not reply with a HB ACK to the same station more than once every 55 minutes.
* **Hold PTT between frames of multi-frame messages:** Keeps the transmitter keyed continuously across frame boundaries during multi-frame transmissions instead of unkeying between frames. This only applies to TCI connected radios with CAT control.

---

## Support and Links

* **User Guide: this document**
* **Support:** via the issues list at [JS8Call-Mobile](https://github.com/Chris-AC9KH/JS8Call-Mobile/issues)
* [**Privacy Policy**](PRIVACY.html)

---

## Acknowledgments & Licenses

* **JS8Call-Mobile** is licensed under the **BSD 3-Clause License**. See [`LICENSE`](LICENSE.html) for full details.
* Built using **[JS8Core](https://github.com/JS8Call-improved/JS8Core)**, licensed under the **MIT License** (Copyright © 2025 js8core contributors, © 2018 Jordan Sherer, © 2026 JS8Call Official).


# Sentry Radio 📡

**Sentry Radio** is a professional-grade Android forensic tool designed to detect, analyze, and map cellular network anomalies, including potential IMSI Catchers (Stingrays), cell site simulators, and suspicious network downgrades.

Built for security researchers and privacy-conscious users, it provides deep insights into the radio stack, monitoring both SIM slots in real-time.

**Version 0.2.0 - Now with enhanced security hardening and API protection.**

---

## 🚀 Key Features

- **🛡️ Real-time Threat Detection:** Monitors for encryption deactivation, silent SMS, and suspicious cell handovers.
- **🚨 Full-screen Overlay Alarms:** Critical alerts now appear over all apps and on the lock screen for immediate notification.
- **📊 Advanced Radio Metrics:** Tracks PCI, EARFCN, Signal Strength (RSSI/RSRP), Timing Advance, and Neighboring cells.
- **🌐 Forensic Mapping:** Visualize detected cell towers and your movement on an offline-capable map using OSMDroid.
- **📡 Dual SIM Support:** Full monitoring for multi-slot devices.
- **🔍 Database Verification:** Cross-references cell data with OpenCellID, Unwired Labs, and BeaconDB to identify "fake" towers.
- **🛠️ Root-Powered Monitoring:** Utilizes root access to sniff the radio logcat and execute low-level telephony dumps.
- **💾 PCAP Export:** Export radio events to GSMTAP-compatible PCAP files for further analysis in Wireshark.
- **🔐 Encrypted Credentials:** API keys and sensitive data now encrypted with AES-256-GCM in Android Keystore.
- **📍 Certificate Pinning:** All API connections protected against MITM attacks with public key pinning.
- **🛡️ Input Validation:** Comprehensive protection against injection and malformed data attacks.

---

## 🛠️ Requirements

- **Android 10 (API 29) or higher.**
- **Root Access:** Required for deep radio logcat monitoring and low-level diagnostic data.
- **(Optional) Xposed/LSPosed:** For enhanced API hooking and stealth.
- **Permission:** "Display over other apps" (SYSTEM_ALERT_WINDOW) for full-screen alarm overlays.

---

## 📥 Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/fzer0x/SentryRadio.git
   ```
2. Open in **Android Studio** and build the project.
3. Install the APK on your rooted device.
4. Grant Root/Superuser permissions when prompted.
5. **Enable "Display over other apps"** in the app settings to allow full-screen alarms.

---

## ⚙️ Configuration

Add your API keys in the app settings (now encrypted in Keystore):
- [OpenCellID API Key](https://opencellid.org/)
- [Unwired Labs Token](https://unwiredlabs.com/)
- BeaconDB (API-Keyless)

**v0.2.0:** API keys are automatically encrypted with AES-256-GCM.

---

## 🛡️ Security (v0.2.0)

Sentry Radio now includes better security hardening:

- **API Key Encryption:** AES-256-GCM encryption in Android Keystore
- **Certificate Pinning:** Public key pinning prevents MITM attacks on all APIs
- **Input Validation:** All data validated before processing
- **Full-screen Overlay Alarms:** Critical security alerts are displayed over other apps and on the lock screen.
- **Safe Root Execution:** Commands executed with timeout and resource limits
- **Audit Logging:** Security events logged for forensic analysis
- **Thread-Safe Code:** Race conditions eliminated, memory leaks fixed

---

## 🔐 Security Tab (v0.2.0)

New interactive security controls in dedicated Security tab:

- **Block GSM Registrations:** Forcefully prevent connections to 2G/GSM networks to mitigate downgrade attacks. When enabled, GSM registration attempts are rejected and the device is kept on LTE/5G.

- **Reject A5/0 Cipher:** Reject connections if the network requests A5/0 (No Encryption). If detected, the app forces a radio cycle to break the unencrypted connection and reconnect with ciphering enabled.

- **Threats Blocked Dashboard:** Shows real-time count of successfully blocked attacks with detailed logs:
  - GSM Downgrade attempts blocked
  - A5/0 (unencrypted) connections blocked
  - Silent SMS (Type-0) attempts detected

- **Blocking Events Log:** Complete history of blocked security threats with timestamps and severity levels. Includes options to unblock cells or clear logs.

---

## 📱 User Interface Tabs

Sentry Radio features a comprehensive tabbed interface:

### 1. **Status Tab** - Real-time Dashboard
- Live threat detection with color-coded severity levels
- SIM slot switching (Dual SIM support)
- Root access status indicator
- Real-time metrics: Signal strength, Timing Advance, Neighbor cell count
- Threat gauge showing overall risk level

### 2. **Map Tab** - Forensic Mapping
- Interactive offline map (OSMDroid) showing all detected cell towers
- Cell tower markers with color-coded status:
  - 🟢 Verified towers in database
  - 🟡 Towers with variable location data
  - 🔴 Missing/fake towers not in database
  - 🔒 Blocked towers
- Auto-sync with API databases (BeaconDB, OpenCellID, UnwiredLabs)
- Zoom to current location or first detected tower
- Tower details on click (coordinates, samples, range, etc.)

### 3. **Audit Tab** - Event Timeline & History
- Complete chronological log of all detected threats
- Filter by SIM slot
- Click events for detailed analysis
- Color-coded event types (IMSI Catcher, Silent SMS, Downgrade, etc.)
- Includes raw logcat captures for forensic analysis
- Block/Unblock cells directly from event view
- Copy raw data to clipboard

### 4. **Security Tab** - Active Defense Controls
- **Block GSM Registrations** - Prevent 2G/GSM network downgrades
- **Reject A5/0 Cipher** - Block unencrypted connections
- **Threats Blocked Dashboard** - Real-time statistics of blocked attacks
- **Blocking Events Log** - Full history of security actions taken
- Unblock All / Delete Blocked buttons

### 5. **Analytics Tab** - Advanced Threat Analysis
- **Threat Summary** - Counts by type (signal, baseband, RRC, handover)
- **Handover Analysis** - Total handovers, anomalies, ping-pong events
- **Network Capability Analysis** - Network degradation detection
- **Signal Anomaly Detection** - Unrealistic signal jumps and interference

### 6. **Settings Tab** - Configuration & Logging Control
- **Database Settings:** API keys for OpenCellID, Unwired Labs, BeaconDB
- **Detection Sensitivity:** Slider to adjust threat detection threshold
- **Mark Fake Cells:** Flag unverified towers as suspicious
- **Logging Options:**
  - Log Radio Metrics (signal, timing advance, etc.)
  - Log Suspicious Events (IMSI Catcher alerts)
  - Log Root Signal Feed (low-level modem data)
  - Show Blocked Events (forensic history)
- **Alarm Control:** Enable/disable vibration alerts

---

## 💾 Export & Analysis Features

- **PCAP Export:** Export all detected events in GSMTAP-compatible PCAP format for analysis in Wireshark
- **Forensic Copy:** Copy raw logcat captures to clipboard for external analysis
- **Clear Logs:** Delete all event history when needed

## 🔄 API Integration

Live database verification against multiple cell tower databases:

- **BeaconDB:** Open-source cell tower database (API-Keyless option available)
- **OpenCellID:** Global cell tower database with crowdsourced data
- **Unwired Labs:** Commercial geolocation service with high accuracy

All API communications are now protected with:
- Certificate pinning to prevent MITM attacks
- Encrypted credentials in Android Keystore
- Request timeouts and rate limiting
- Comprehensive audit logging of all API calls

---

## 🛡️ Security Analysis Layers

Sentry Radio analyzes several layers of the cellular protocol:
- **Physical Layer:** Unrealistic signal jumps or timing advance values.
- **Protocol Layer:** RRC state transitions and Location Update Rejects.
- **Security Layer:** Monitoring for Ciphering indicator (A5/0) and silent paging.
- **Baseband Layer:** Fingerprinting of known vulnerable modem firmware.

---

## 🤝 Contributing

Contributions are welcome! For major changes, please open an issue first.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

**Security Issues:** Please report security vulnerabilities responsibly, not via public issues.

---

## ⚖️ License

Distributed under the GNU GPL v3 License. See `LICENSE` for more information.

---

## 📝 Changelog

**v0.2.0** (February 2026)
- Added security hardening (8 new security modules)
- **Full-screen Overlay Alarms** (requires SYSTEM_ALERT_WINDOW permission)
- Certificate pinning for all APIs
- AES-256-GCM encryption for API keys in Keystore
- Input validation framework
- Comprehensive audit logging
- Memory leak prevention
- Thread-safe operations
- **New Security Tab with active threat blocking:**
  - Block GSM Registrations (prevents 2G downgrade attacks)
  - Reject A5/0 Cipher (blocks unencrypted connections)
  - Threats Blocked Dashboard (real-time blocking statistics)
  - Blocking Events Log (detailed forensic history)

**v0.1.0** (Initial Release)
- Basic IMSI Catcher detection
- Real-time threat monitoring
- Forensic mapping

---

## ⚠️ Disclaimer

*This tool is for educational and research purposes only. Monitoring cellular networks may be subject to legal restrictions in some jurisdictions. The developer assumes no liability for misuse.*

**Developed with ❤️ by [fzer0x](https://github.com/fzer0x)**

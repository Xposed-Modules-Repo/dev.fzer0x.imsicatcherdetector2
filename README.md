# 📡 Sentry Radio

> **Sentry Radio** is a **professional-grade Android forensic platform** for detecting, analyzing, and mapping cellular network threats — including **IMSI Catchers (Stingrays)**, **fake base stations**, and **covert downgrade attacks**.  
Built for **security researchers, journalists, and privacy-critical users**, it provides deep, real-time visibility into the **cellular radio stack** across **both SIM slots**.

---

# 🚀 Core Capabilities

## 🛡️ Real-Time Threat Detection
- Detects **ciphering deactivation (A5/0)**
- Flags **silent SMS**
- Identifies **rogue cell handovers**
- Detects **suspicious downgrades (LTE → 2G)**

## 📊 Advanced Radio Telemetry
- PCI, EARFCN  
- RSSI, RSRP, RSRQ  
- Timing Advance  
- Neighboring cell topology  

## 🌐 Forensic Mapping
- Offline-capable **OSMDroid map**
- Live tracking of:
  - Cell towers
  - Movement paths
  - Anomaly locations

## 📡 Dual-SIM Surveillance
- Independent monitoring of **both modems**
- Detects asymmetric attacks targeting only one SIM

## 🔍 Tower Authenticity Verification
Cross-checks observed cells against:
- **OpenCellID**
- **Unwired Labs**
- **BeaconDB**

Flags **ghost towers** and **cell site simulators**

## 🛠️ Root-Level Telemetry
- Baseband logcat sniffing
- Telephony service dumps
- RIL message inspection
- Firmware fingerprinting

## 💾 PCAP Export
- Exports **GSMTAP-compatible PCAP**
- Works with **Wireshark, tshark, and forensic toolchains**

---

# 🛠️ System Requirements

| Component | Requirement |
|----------|------------|
| OS | Android 10+ (API 29+) |
| Root | **Required** |
| Xposed / LSPosed | Optional |
| Device | Qualcomm-based phones recommended |

---

# 📥 Installation

git clone https://github.com/fzer0x/SentryRadio.git

1. Open in **Android Studio**  
2. Build the APK  
3. Install on a **rooted device**  
4. Grant **Superuser** permissions  

---

# ⚙️ Configuration

To enable **live cell verification**, add API keys in **App Settings**:

| Service | URL |
|--------|-----|
| OpenCellID | https://opencellid.org |
| Unwired Labs | https://unwiredlabs.com |

These allow Sentry Radio to detect:
- Real carrier towers  
- Rogue IMSI catchers  
- Cell site simulators  

---

# 🛡️ Security Analysis Engine

Sentry Radio correlates anomalies across multiple radio layers:

## 📶 Physical Layer
- Impossible signal jumps  
- Invalid timing advance  
- Cell teleportation  

## 📡 Protocol Layer
- RRC state abuse  
- Location Update Rejects  
- Attach failures  
- Paging manipulation  

## 🔐 Security Layer
- Ciphering disabled (A5/0)  
- Fake encryption flags  
- Silent paging  

## 🧠 Baseband Layer
- Modem firmware fingerprinting  
- Vulnerable chipset detection  
- Rogue network profiling  

---

# 🤝 Contributing

We welcome all contributions.

git checkout -b feature/AmazingFeature  
git commit -m "Add AmazingFeature"  
git push origin feature/AmazingFeature  

Then open a **Pull Request**

---

# ⚖️ License

Distributed under the **GNU GPL v3 License**  
See `LICENSE` for details.

---

# ⚠️ Legal Disclaimer

This software is for **research, journalism, and defensive security**.

Monitoring cellular networks may be restricted in some countries.  
You are responsible for compliance with local law.

The author assumes **no liability** for misuse.

---

# ❤️ Credits

Developed by **fzer0x**  
https://github.com/fzer0x

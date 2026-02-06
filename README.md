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
|--------|------------|
| OS | Android 10+ (API 29+) |
| Root | **Required** |
| Xposed / LSPosed | Optional |
| Device | Qualcomm-based phones recommended |

---

# 📥 Installation

```bash
git clone https://github.com/fzer0x/SentryRadio.git

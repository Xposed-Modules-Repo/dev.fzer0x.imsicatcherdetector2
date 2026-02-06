Sentry Radio 📡
Sentry Radio is a professional-grade Android forensic tool designed to detect, analyze, and map cellular network anomalies, including potential IMSI Catchers (Stingrays), cell site simulators, and suspicious network downgrades.
Built for security researchers and privacy-conscious users, it provides deep insights into the radio stack, monitoring both SIM slots in real-time.

🚀 Key Features
🛡️ Real-time Threat Detection: Monitors for encryption deactivation, silent SMS, and suspicious cell handovers.
📊 Advanced Radio Metrics: Tracks PCI, EARFCN, Signal Strength (RSSI/RSRP), Timing Advance, and Neighboring cells.
🌐 Forensic Mapping: Visualize detected cell towers and your movement on an offline-capable map using OSMDroid.
📡 Dual SIM Support: Full monitoring for multi-slot devices.
🔍 Database Verification: Cross-references cell data with OpenCellID, Unwired Labs, and BeaconDB to identify “fake” towers.
🛠️ Root-Powered Monitoring: Utilizes root access to sniff the radio logcat and execute low-level telephony dumps.
💾 PCAP Export: Export radio events to GSMTAP-compatible PCAP files for further analysis in Wireshark.

🛠️ Requirements
Android 10 (API 29) or higher.
Root Access: Required for deep radio logcat monitoring and low-level diagnostic data.
(Optional) Xposed/LSPosed: For enhanced API hooking and stealth.

📥 Installation
Clone the repository:
git clone https://github.com/fzer0x/SentryRadio.git 
Open the project in Android Studio.
Build and install the APK on your rooted device.
Grant Root/Superuser permissions when prompted.

⚙️ Configuration
To enable live database verification, add your API keys in the app settings:
OpenCellID API Key (https://opencellid.org/)
Unwired Labs Token (https://unwiredlabs.com/)

🛡️ Security Analysis Layers
Sentry Radio analyzes several layers of the cellular protocol:
Physical Layer: Unrealistic signal jumps or timing advance values.
Protocol Layer: RRC state transitions and Location Update Rejects.
Security Layer: Monitoring for Ciphering indicator (A5/0) and silent paging.
Baseband Layer: Fingerprinting of known vulnerable modem firmware.

🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.
Fork the Project
Create your Feature Branch (git checkout -b feature/AmazingFeature)
Commit your Changes (git commit -m 'Add some AmazingFeature')
Push to the Branch (git push origin feature/AmazingFeature)
Open a Pull Request

⚖️ License
Distributed under the GNU GPL v3 License. See LICENSE for more information.

⚠️ Disclaimer
This tool is for educational and research purposes only. Monitoring cellular networks may be subject to legal restrictions in some jurisdictions. The developer assumes no liability for misuse.
Developed with ❤️ by fzer0x (https://github.com/fzer0x)

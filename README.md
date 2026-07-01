# Aircracking: Modern Wi-Fi Security Testing Guide

[![Last Updated](https://img.shields.io/badge/Last%20Updated-July%202026-blue)](https://github.com/nova0408-glitch/Aircracking)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Educational guide for testing WPA/WPA2 (and PMKID) Wi-Fi network security using Aircrack-ng, Hashcat, and hcxtools.**

> **⚠️ LEGAL DISCLAIMER**  
> This material is provided for **educational and authorized penetration testing purposes only**. Unauthorized access to wireless networks is illegal in most jurisdictions. Only test networks you own or have explicit written permission to test. The author and contributors are not responsible for any misuse.

## Features
- Updated for 2026 tools (Aircrack-ng ~1.7+, latest Hashcat, hcxtools/hcxdumptool)
- Passive & active methods (including PMKID)
- GPU-accelerated cracking
- Hardware recommendations + troubleshooting
- Full hcxtools workflow (recommended)

## Table of Contents
- [Getting Started](#getting-started)
- [Recommended Modern Workflow](#recommended-modern-workflow)
- [Basic Aircrack-ng Workflow](#basic-aircrack-ng-workflow)
- [Cracking](#cracking)
- [Advanced Techniques](#advanced-techniques)
- [Troubleshooting](#troubleshooting)
- [Legal & Ethical Notes](#legal--ethical-notes)

## Getting Started

### Prerequisites
- **Kali Linux** (or Debian-based with tools installed)
- Wireless adapter with **monitor mode + packet injection** support:
  - Recommended: Alfa AWUS036AXM / AWUS036AXML (Wi-Fi 6/6E), AWUS036ACH
- Install tools:
  ```bash
  sudo apt update && sudo apt install aircrack-ng hashcat hcxtools hcxdumptool wireshark

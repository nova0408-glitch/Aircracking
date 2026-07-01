# Appendix

Additional techniques and community contributions.

## Modern Capture with hcxdumptool (Recommended)
```bash
# Passive-ish aggressive capture
sudo hcxdumptool -i wlan0mon -o capture.pcapng -t 5 --enable_status=15
hcxpcapngtool -o hash.22000 capture.pcapng

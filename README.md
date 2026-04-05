# DiGi Gate V2 OLED Display for AllStarLink

A professional OLED display driver for Raspberry Pi based AllStarLink (ASL) nodes. This software provides real-time status, IP address, WiFi strength, and connected node information on an SSD1306 OLED display.

## Quick Installation

To install or update your DiGi Gate V2 OLED software, run the following commands on your Raspberry Pi:

### 1. Update and Prepare System
First, ensure your system is up to date and any pending configurations are resolved:
```bash
sudo apt update && sudo apt upgrade -y
sudo dpkg --configure -a
```

### 2. Download the Installer
Download the latest production-ready `.deb` package from GitHub:
```bash
wget https://github.com/fahadmieaji/digi_gate_oled/raw/refs/heads/main/digi-gate-v2.deb
```

### 3. Install the Package
Run the installer. During this process, you will be asked to enter your **Callsign** and **Node Number**:
```bash
sudo apt install ./digi-gate-v2.deb
```

## Management Commands

### Check Service Status
To see if the display driver is running correctly:
```bash
systemctl status digi-gate.service
```

### View Live Logs
To monitor the display activity and troubleshoot connections:
```bash
journalctl -u digi-gate.service -f
```

### Update Configuration
If you need to change your Callsign or Node Number later without reinstalling:
```bash
sudo nano /etc/digi-gate/config.json
```
*After editing, save (Ctrl+O, Enter) and exit (Ctrl+X), then restart the service:*
```bash
sudo systemctl restart digi-gate.service
```

---
**Made in Bangladesh by [TORUN](http://www.torun.com.bd)**

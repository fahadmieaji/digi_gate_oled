# DiGi Gate V2 - OLED Display for AllStarLink

DiGi Gate V2 is a professional OLED display driver designed for AllStarLink (ASL) nodes. It provides real-time status monitoring, network information, and an interactive CLI-based configuration menu.

## Features

- **Real-time Monitoring**: Displays Callsign, Node Number, IP Address, and WiFi strength.
- **ASL Status**: Shows RX/TX status and a list of currently connected nodes (links).
- **CLI Configuration Menu**: Easily change settings via terminal without editing files manually.
- **180° Screen Rotation**: Support for inverted display mounting via software toggle.
- **Screensaver Mode**: Bouncing text animation to prevent OLED burn-in after 30 seconds of inactivity.
- **Optimized for ASL3**: Fully compatible with AllStarLink 3 (Debian Bookworm).
  
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

## Configuration

Once installed, you can manage your DiGi Gate V2 using the built-in CLI menu.

### Opening the Menu
Simply type the following command in your terminal:

```bash
sudo digi-gate-menu
```

### Menu Options
1. **Change Callsign**: Update the displayed callsign.
2. **Change Node Number**: Update the AllStar node being monitored.
3. **Toggle Rotation**: Rotate the screen text 180 degrees (Inverted mode).
4. **Save and Apply**: Persist changes and restart the display service.

## Manual Configuration
Settings are stored in JSON format at:
`/etc/digi-gate/config.json`

Example:
```json
{
    "callsign": "S21AF",
    "node": "1234",
    "rotation": 2
}
```
*(Rotation: 0 = Normal, 2 = 180° Inverted)*

## Service Management
The display runs as a systemd service. You can control it using:

- **Restart**: `sudo systemctl restart digi-gate.service`
- **Stop**: `sudo systemctl stop digi-gate.service`
- **Logs**: `journalctl -u digi-gate.service -f`

## Hardware Requirements
- Raspberry Pi (running AllStarLink)
- SSD1306 128x64 I2C OLED Display
- I2C enabled on the Pi (handled by installer)


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
**Developed by TORUN**  
[www.torun.com.bd](http://www.torun.com.bd)  
Made in Bangladesh


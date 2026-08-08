# LoRaWAN Industrial Site Monitoring Demo

Industrial HMI demonstration for **Elecrow CrowPanel ESP32-P4 panels**, hardware revision **V1.2**. The application presents a beverage production and bottling plant with 60 LoRaWAN devices across six connected production areas.

## Installation

### Requirements

- Elecrow CrowPanel ESP32-P4, hardware revision **V1.2**;
- Windows computer;
- data-capable USB-C cable.

### Flash the Panel

1. [Download `CrowPanel_P4_flasher.zip`](./CrowPanel_P4_flasher.zip).
2. Fully extract the ZIP archive.
3. Connect the panel's **UART0 USB-C port** to the computer.
4. Open the extracted `CrowPanel_P4_flasher` folder.
5. Run `CrowPanel_P4_flasher.exe`.
6. Select the panel's COM port. Click **Refresh** if it is not listed.
7. Enable **Clean install (erase entire flash)**.
8. Click **Flash panel** and wait for **Firmware installed successfully**.

The panel restarts automatically after installation.

## Documentation

- [System Overview](./SYSTEM_OVERVIEW.md)
- [User Manual](./USER_MANUAL.md)

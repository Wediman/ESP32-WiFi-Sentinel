# 🚀 Setup Guide

## What you need on your computer

- A USB cable that carries **data** (not charge-only)
- [Python](https://www.python.org/) with `esptool` (`pip install esptool`)
- [Thonny](https://thonny.org/) (easiest), or `mpremote` (`pip install mpremote`)

## Step 1: Flash MicroPython (one time only)

1. Download the latest **ESP32_GENERIC** firmware (`.bin`) from [micropython.org/download/ESP32_GENERIC](https://micropython.org/download/ESP32_GENERIC/).
2. Plug in the ESP32. Find its port (`COM3` on Windows, `/dev/ttyUSB0` on Linux, etc.).
3. Erase, then flash:

```bash
esptool.py --chip esp32 --port COM3 erase_flash
esptool.py --chip esp32 --port COM3 --baud 460800 write_flash -z 0x1000 firmware.bin
```

> Use your real port name and the real `.bin` file name.

## Step 2: Upload the code

**Option A: Thonny**
1. Tools → Options → Interpreter → **MicroPython (ESP32)** → pick your port.
2. Open `main.py`.
3. File → Save as → **MicroPython device** → name it `main.py`.

**Option B: mpremote**
```bash
mpremote connect COM3 cp main.py :main.py
```

## Step 3: Run it

Press the **EN/RESET** button on the ESP32. A file named `main.py` runs automatically every time the board powers up.

> ✋ The screen says **"Hands off stick!"** at boot. Don't touch the joystick for about one second so it can find its center.

You can now power it from a USB power bank and carry it around.

## Troubleshooting

| Problem | Fix |
|---------|-----|
| LCD is blank or shows only solid blocks | Turn the **contrast pot**. Also check the 5V and GND wires on LCD pins 1, 2, 5, 15, 16. |
| Backlight is on but no text | Re-check RS, E, D4-D7 wires against the [pin table](wiring.md). |
| Garbled characters | A data wire (D4-D7) is loose or swapped. |
| Joystick moves by itself | Reboot and **don't touch the stick** during calibration. Make sure joystick VCC is on **3V3**. |
| Left/right and up/down feel swapped | Swap the VRX and VRY pin numbers at the top of `main.py`. |
| "No networks" | The ESP32 sees **2.4 GHz only**. Move closer to a router, then **hold the button** to rescan. |
| Thonny can't find the board | Try another USB cable, install the USB driver (CP210x or CH340), or hold the BOOT button while connecting. |
| Code won't run at power-up | Make sure the file on the board is named exactly `main.py`. |

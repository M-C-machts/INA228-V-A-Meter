# INA228-V-A-Meter

A KiCad 9 hardware project for a compact voltage and current meter/logger using:
- **TI INA228** - high-accuracy current/voltage/power monitor
- **Seeed XIAO ESP32-C3** - MCU module

The board is **powered from a LiFePO₄ battery** and charged via the **XIAO's USB-C port**.

> **Status:** Work in progress. Some changes may occur.

---

## Features
- Simultaneous **bus voltage** and **current** measurement via INA228
- ESP32-C3 firmware
- LiFePO₄ battery powered - portable
- 1.3" OLED display

---

## Hardware Overview
### Main Components
- **INA228**: measures shunt and bus voltage; performs current/power calculations internally
- **XIAO ESP32-C3**: reads INA228 over **I²C** and outputs/logs data
- LiFePO₄ charge/discharge power management is handled via a daughter board: [XIAO-LiFePO4-Power-Module](https://github.com/M-C-machts/XIAO-LiFePO4-Power-Module)
- Gerber files for PCB fabrication are included
- Case files for 3D printing are included

### Power
- The board is powered by a **LiFePO₄ cell**.
- Charging is handled **through the XIAO USB-C port** via the daughter board. The XIAO's onboard charger/power path is not used.
- To use a LiPo battery instead, omit the XIAO-LiFePO4-Power-Module and connect a *protected* LiPo battery directly to the XIAO battery solder pads.

---

## Firmware
- Reads INA228 registers via I²C
- Calculates and displays:
  - Voltage (V)
  - Current (A)
  - Power (W) *(optional)*
- Outputs data over USB serial and 1.3" OLED display



## Calibration / Accuracy Notes
INA228 measurement accuracy depends heavily on:
- Shunt resistor value, tolerance, and temperature coefficient
- Correct INA228 configuration (averaging, conversion times, calibration register)


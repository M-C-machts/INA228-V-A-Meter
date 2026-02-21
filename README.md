# INA228-V-A-Meter

KiCad 9 hardware project for a compact voltage + current meter/logger using:
- **TI INA228** (high-accuracy current/voltage/power monitor)
- **Seeed XIAO ESP32-C3** (MCU module)

The board is **powered from a LiFePO₄ battery** and is intended to be **charged via the XIAO’s USB-C port**.

> Status: work in progress. Expect changes.

---

## Features (planned / target)
- Simultaneous **bus voltage** + **current** measurement via INA228
- ESP32-C3 firmware
- Battery powered (LiFePO₄), portable
- 1.3" OLED Display

---

## Hardware overview
### Main components
- **INA228**: measures shunt voltage + bus voltage, supports current/power calculations internally
- **XIAO ESP32-C3**: reads INA228 over **I²C** and outputs/logs data

### Power
- **LiFePO₄ cell** powers the board.
- Charging is intended **through the XIAO USB-C** via a daughter board (the XIAO’s onboard charger/power path is NOT used).

---

## Firmware (planned)
- Read INA228 registers via I²C
- Convert to:
  - Voltage (V)
  - Current (A)
  - Power (W) (optional)
- Output over USB serial and 1,3" OLED Display



## Calibration / accuracy notes
INA228 accuracy depends heavily on:
- Shunt resistor value + tolerance + temperature coefficient
- Correct INA228 configuration (averaging, conversion times, calibration register)


# Smart LiFePO₄ Battery Charging and UPS Backup System

**Hardware prototype and technical roadmap** | Electrical & Embedded Systems

**Project by Hareram Kumar** | Jadavpur University | 2026

## Overview

This laboratory project explores a microcontroller-monitored smart battery charging and DC backup system. The implemented prototype focuses on the **mains-isolated AC-to-DC power front end, sensor acquisition, manual buck conversion and buzzer alerts**, validated using a **10 Ω dummy resistor**. **A live LiFePO₄ battery pack and UPS backup transfer were not experimentally demonstrated** in the technical report.

### Components documented in the implemented prototype

| Stage | Component / technology | Purpose |
| --- | --- | --- |
| AC input | 230 V AC to 18 V AC transformer | Isolated step-down power |
| Rectifier | KBPC3510 single-phase bridge | Full-wave rectification |
| Protection | Inline fuse and manual isolation switch | Electrical protection/isolation |
| DC smoothing | 2200 µF filter capacitor | Ripple smoothing |
| DC-DC converter | LM2596 module | Manually adjustable buck regulation |
| MCU | Arduino Uno | Monitoring and audible alerts |
| Electrical sensing | INA219 over I²C | Voltage, current and power readings |
| Temperature sensing | DS18B20 over 1-Wire | Temperature readings |
| Alerting | Active buzzer | Fault indication during bench testing |

## Dummy-load validation reported

The following values are **taken from the project report**, not independently measured or reproduced here:

| Buck setpoint | Current | Power | Status |
| --- | --- | --- | --- |
| 3.30 V | 0.330 A | 1.09 W | Normal, 28.4 °C |
| 3.65 V | 0.365 A | 1.33 W | Normal, 30.1 °C |
| 4.35 V | 0.435 A | 1.89 W | >4.2 V alarm triggered |

These observations use a 10 Ω resistor. They **do not verify lithium-cell charging, state-of-health diagnostics, battery management system operation or seamless UPS transfer**.

## Architecture

`230 V AC → 18 V transformer → KBPC3510 bridge → fuse & switch → filter capacitor → LM2596 buck → INA219 → resistor load`

`Arduino Uno ← INA219 (I²C) + DS18B20 (1-Wire); Arduino Uno → buzzer alarm`

## Planned Phase II (not implemented in the reported prototype)

- Feedback-controlled CC–CV charging via digital potentiometer or filtered PWM control.
- Arduino-controlled relay cutoff and MOSFET-based battery transfer.
- Live 4S LiFePO₄ pack with dedicated battery management system.
- Local OLED/LCD display and possible ESP32/ESP8266 cloud telemetry.
- Active internal-resistance state-of-health test.

## Documents and images

- [Two-page public case study](case-study.pdf)
- [Full 17-page technical project report](technical-report.pdf): contains planned concepts in addition to tested hardware; do not treat it as a finished UPS product specification.
- [Laboratory prototype photograph](laboratory-prototype.jpg)
- [Arduino and sensor instrumentation photograph](instrumentation-closeup.jpg)

**Note:** The technical report includes an illustrative, incomplete Arduino source extract. No complete, independently compiled firmware is being published in this repository. Safety-sensitive electrical designs should be reviewed and tested by a qualified supervisor before any battery or mains-connected use.

## Portfolio

[Hareram Kumar's portfolio](https://hareramkumarportfolioreadytodeploy.vercel.app/)

# Mesh-Hardware

Open-source hardware designs for [Meshtastic](https://meshtastic.org) — PCB files, EEPROM images, and radio configs for LoRa nodes and Pi HATs.

---

## Projects

### DoubleHat — Dual Radio Raspberry Pi HAT

A Raspberry Pi HAT+ carrying two LoRa radios, dual GPS, and dual AHT20 temperature/humidity sensors. Available in two variants depending on the radio module used:

| Directory                                  | Module                       | Chip            |
|--------------------------------------------|------------------------------|-----------------|
| [DoubleHat/NiceRFLR/](DoubleHat/NiceRFLR/) | NiceRF LR1121F33 / LR2021F33 | LR1121 / LR2021 |
| [DoubleHat/EbyteE22/](DoubleHat/EbyteE22/) | Ebyte E22 / E22P             | SX1262          |

### NiceFox — NiceRF LR2021F33 Hat for LuckFox Ultra

A compact single-radio LoRa hat for the LuckFox Pico Ultra and LuckFox Lyra Ultra SBCs.

| Directory            | Module           | Chip   |
|----------------------|------------------|--------|
| [NiceFox/](NiceFox/) | NiceRF LR2021F33 | LR2021 |

### 1.25 Meter SX1262 Module — 222–225 MHz mikroBUS LoRa Module

A mikroBUS-format LoRa add-on board tuned for the US amateur 1.25 meter band (222–225 MHz), built around a bare SX1262.

| Directory                                                     | Module | Chip   |
|----------------------------------------------------------------|--------|--------|
| [1.25 Meter SX1262 Module/](1.25%20Meter%20SX1262%20Module/) | SX1262 | SX1262 |

---

## License

This work is licensed under the **[CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S v2)](LICENSE.md)**.

You are free to use, study, modify, and distribute these designs and products made from them, provided that any Product embodying this Licensed Material — or Modifications of it — is made available under the same licence, with corresponding source made available per Section 5.

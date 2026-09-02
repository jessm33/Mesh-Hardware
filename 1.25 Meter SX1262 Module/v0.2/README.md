# 1.25 Meter (222–225 MHz) SX1262 mikroBUS Module — v0.2 (archived)

> **This is an archived hardware revision.** For the current release, see the [top-level README](../README.md).

A mikroBUS-format LoRa add-on board built around the Semtech **SX1262**, front-end tuned for the US amateur **1.25 meter band (222–225 MHz)**. The board edge follows the mikroBUS pinout; solder a pin header (or castellated edge-mount) onto the module to plug it into a mikroBUS socket.

Being a standard mikroBUS module, it's compatible with MCU carrier boards such as [NomDeTom/Modular_MeshMess](https://github.com/NomDeTom/Modular_MeshMess).

---

## PCB

![PCB](v0.2/3D_PCB1_2026-07-31.png)

---

## Hardware Revisions

| Version | Directory | Notes |
|---------|-----------|-------|
| v0.2 | [v0.2/](v0.2/) | Current release |

---

## Ordering PCBs from JLCPCB

The [v0.2/](v0.2/) directory contains all files needed to order assembled boards from [JLCPCB](https://jlcpcb.com).

### Files

| File | Purpose |
|------|---------|
| [Gerber_PCB1_2026-07-31.zip](v0.2/Gerber_PCB1_2026-07-31.zip) | Gerber files for PCB fabrication |
| [BOM_Board1_PCB1_2026-07-31.csv](v0.2/BOM_Board1_PCB1_2026-07-31.csv) | Bill of materials for JLCPCB SMT assembly |
| [PickAndPlace_PCB1_2026-07-31.csv](v0.2/PickAndPlace_PCB1_2026-07-31.csv) | Component placement file for SMT assembly |
| [ProPrj_sx1262 125cm v0.2_2026-07-31.epro](v0.2/ProPrj_sx1262%20125cm%20v0.2_2026-07-31.epro) | EasyEDA Pro source project |

### Steps

1. Go to [jlcpcb.com](https://jlcpcb.com) and click **Order Now**.
2. Upload `Gerber_PCB1_2026-07-31.zip`. JLCPCB will auto-detect the board dimensions.
3. Set your desired quantity and any stack-up/colour preferences (defaults are fine).
4. Enable **PCB Assembly (PCBA)** and select **Standard PCBA**.
5. Upload `BOM_Board1_PCB1_2026-07-31.csv` and `PickAndPlace_PCB1_2026-07-31.csv` when prompted.
6. Confirm component matches — every part, including the SX1262 itself, is sourced from LCSC and should resolve automatically.
7. Review the component placement preview, then proceed to checkout.

> **Note:** Unlike the other boards in this repo, the SX1262 here is placed as a bare die-down part (not a pre-made castellated module), so it **is** available for JLCPCB assembly — no hand soldering required for the RF section.

> **Note:** The mikroBUS edge (MB1), plus breakout headers **H1** and **H2**, are unpopulated 2.54 mm through-hole pads — none of them are in the SMT BOM. Solder a pin header onto MB1 to plug the board into a mikroBUS socket, and solder headers or wires to H1/H2 only if you need those signals broken out.

---

## mikroBUS Pinout

| mikroBUS Pin | Net | Function |
|---------------|-----|----------|
| AN | — | Not connected to the SX1262 (spare) |
| RST | NRESET | SX1262 reset |
| CS | NSS | SPI chip select |
| SCK | SCK | SPI clock |
| MISO | MISO | SPI MISO |
| MOSI | MOSI | SPI MOSI |
| 3.3V | VCC | 3.3 V supply in |
| GND | GND | Ground |
| GND | GND | Ground |
| 5V | — | Not connected to the SX1262 (spare) |
| SDA | — | Not connected |
| SCL | — | Not connected |
| TX | — | Not connected |
| RX | — | Not connected |
| INT | DIO1 (IRQ) | SX1262 interrupt |
| PWM | BUSY | SX1262 busy status |

### Breakout headers (unpopulated)

| Header | Pins | Signal |
|--------|------|--------|
| H1 | 5-pin, 2.54 mm | GND, AN, TX, 3.3V (VCC), RFS (DIO2) |
| H2 | 2-pin, 2.54 mm | VCC, SX PWR (SX_VCC — in series with the L1 supply choke; useful for measuring SX1262 current draw or injecting a filtered rail) |

---

## RF Front End

DIO2 drives the **SKY13453-385LF** SP3T RF switch through an L/C harmonic filter network (L7–L9, C24–C29) tuned for 222–225 MHz, feeding the SMA antenna jack (CN1). An **EZAEG2N50AX** TVS diode protects the antenna line.

### TX matching filter simulation

The output matching/harmonic filter (L1, C1–C3, LC1) was modeled in SimNEC against a 50 Ω load. The source project is [txsx1262v2.ssn](v0.2/txsx1262v2.ssn); a capture of the simulated response is [simnec0.2.gif](v0.2/simnec0.2.gif):

![SimNEC TX matching filter simulation](v0.2/simnec0.2.gif)

At the 223 MHz marker the network presents 9+j8 Ω to a 50 Ω source with SWR ≈ 1.19, and the response is a low-pass shape rolling off past ~400 MHz to attenuate harmonics.

---

## Schematic

[SCH_Schematic1_2026-07-31.pdf](v0.2/SCH_Schematic1_2026-07-31.pdf)

---

## License

This work is licensed under the **[CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S v2)](../LICENSE.md)**.

You are free to use, study, modify, and distribute these designs and products made from them, provided that any Product embodying this Licensed Material — or Modifications of it — is made available under the same licence, with corresponding source made available per Section 5.

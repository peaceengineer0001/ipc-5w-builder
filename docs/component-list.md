# Component List — PFGen V5A(R) PCB

## Overview

All components listed below are standard electronic parts available from any reputable electronics supplier. The PCB Gerber files can be manufactured by any PCB fabrication service.

---

## PCB

| Item | Specification | Notes |
|------|--------------|-------|
| PCB | PFGen V5A(R) | Use Gerber zip file with any PCB fabrication service. Minimum order typically 5 boards. |

---

## Resistors (all 1/4W through-hole)

| Part ID | Value | Quantity |
|---------|-------|----------|
| R1 | 6.8kΩ | 1 |
| R2 | 10kΩ | 1 |
| R3 | 6.8kΩ | 1 |
| R4 | 10kΩ | 1 |
| R5 | 15kΩ | 1 |
| R6 | 1MΩ trimmer potentiometer | 1 |
| R7 | 1MΩ trimmer potentiometer | 1 |
| R8 | 18kΩ | 1 |
| R9 | 18kΩ | 1 |
| R10 | 4.7MΩ | 1 |
| R11 | 10kΩ | 1 |
| R12 | 10Ω | 1 |

---

## Capacitors

| Part ID | Value | Voltage Rating |
|---------|-------|----------------|
| C1 | 220nF | 50V |
| C2 | 100µF+ electrolytic | 25V |
| C3 | 100µF+ electrolytic | 25V |
| C4 | 1000µF+ electrolytic | 25V |
| C5 | 1000µF+ electrolytic | 25V |

---

## Semiconductors

| Part ID | Component | Description |
|---------|-----------|-------------|
| Q1 | P2N2222A | NPN transistor |
| D1 | 1N4007 | Rectifier diode |
| D2 | 1N4001 | Rectifier diode |
| U1 | CD4060BE | 14-stage binary counter/oscillator (Decade Counter) |
| U2 | Device Socket | TO-247 10A socket for active device |
| U3 | Neon bulb | Safety bypass indicator |
| LED 1 | Green, 3-5mm | Battery 1 indicator |
| LED 2 | Green, 3-5mm | Battery 2 indicator |
| LED 3 | Red, 3-5mm | Swap indicator |

### Active Devices (choose one — plugs into U2 socket)

| Device | Avalanche Rating | Peak Pulse Voltage | Recommendation |
|--------|-----------------|-------------------|----------------|
| STP20N90K5 | ~900V | ~0.9kV | Good starting point, widely available |
| STW12N170K5 | ~1700V | ~1.7kV | Higher performance, harder to source |
| IRF840 | ~500V | ~0.5-0.6kV | Most common, basic results |

> **Tip:** Start with the STP20N90K5 if available. The CoP > 1 phenomenon is readily apparent above 800-900V. Higher voltage devices push CoP values higher.

---

## Relays

| Part ID | Type | Description |
|---------|------|-------------|
| RLY1 | 16A power relay (40.61 series) | Main battery swap relay |
| RLY2 | HFD2 signal relay (HFD2/012-S-L2-D) | HV signal routing |
| RLY3 | HFD2 signal relay (HFD2/012-S-L2-D) | HV signal routing |

---

## Switches

| Part ID | Type | Function |
|---------|------|----------|
| SW1 | Mini SPDT toggle | Swap time selector (T1/T2) |
| SW2 | Mini SPDT toggle | Swap On/Off |
| SW3 | Mini SPDT toggle | HV Swap/Out |

---

## Connectors & Hardware

| Item | Specification | Quantity |
|------|--------------|----------|
| 2-pin header connectors | Male pin headers, single row | 7 |
| 4-pin header connectors | Made from 2×2-pin slid together | 6 |
| Test point connectors (1×2) | Straight male pin headers | 17 |
| Jumper caps | For use with test point connectors | 7-8 |
| DIP-16 IC sockets | For U1 and relay sockets | 3 |
| PCB feet | Adhesive or screw-mount | 4 |

---

## External Components

| Item | Specification | Notes |
|------|--------------|-------|
| PWM Module | External pulse width modulation unit | Controls pulse frequency and duty cycle |
| Solenoid Coils | 3 required (wound on ferrite/steel cores) | See assembly guide for winding specifications |
| Batteries | 2× matched batteries | LiFePO4 (7-18Ah) recommended, or Pb-acid (40-80Ah) |
| Power Supply | 12V adjustable | For testing (replaces supply battery) |
| Wiring | AWG18 silicone (main), AWG16 (battery), AWG20 (signal) | Various colors recommended |
| Panel Meters | 2× small voltage meters | For monitoring battery voltages |
| Main Switch | SPDT | Master power switch |
| Fuse | Inline fuse holder + appropriate fuse | Safety requirement |

---

## Tools Required

| Tool | Purpose |
|------|---------|
| Soldering iron (temperature controlled) | Component assembly |
| Solder (lead-free recommended) | Joints |
| Multimeter | Voltage, current, continuity testing |
| Heat sink clips | Hold components during soldering |
| Wire strippers | Preparing wire connections |
| Side cutters | Trimming component leads |
| Oscilloscope (optional but recommended) | Viewing pulse waveforms |
| Tachometer (if using rotor) | RPM measurement |

---

## Sourcing Tips

1. Use reputable electronics distributors for critical components (MOSFETs, relays)
2. Standard resistors and capacitors from any supplier are fine
3. Be cautious with unusually cheap active devices — counterfeit components exist
4. The PCB Gerber file works with most fabrication services worldwide
5. Order a few extra PCBs for practice or sharing

---

*Component list maintained by IPC.Engineer — [https://ipc.engineer](https://ipc.engineer)*

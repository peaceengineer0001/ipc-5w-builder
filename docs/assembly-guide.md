# Assembly Guide — 5W PFGen V5A(R) System

## Overview

This guide walks you through building a complete 5W Inductive Pulse Charging system from start to finish. Follow each step in order, and verify your work at each checkpoint before proceeding.

**Estimated build time:** 8-12 hours for a first build

---

## Phase 1: PCB Preparation

### Step 1: Order Your PCB
1. Download the Gerber zip file from this repository
2. Upload it to any PCB fabrication service (do not unzip — upload as-is)
3. Default settings are acceptable; minimum order is typically 5 boards
4. Blue solder mask is recommended for readability

### Step 2: Attach PCB Feet
- Secure 4 feet to the bottom corners of the PCB
- This prevents the underside traces from scratching on your work surface

### Step 3: Print Component List
- Print the component list from [docs/component-list.md](component-list.md)
- Check off each component as you install it — this prevents costly mistakes

---

## Phase 2: Passive Components

### Step 4: Install Terminal Blocks
Install all 2-pin and 4-pin terminal blocks around the board edges:
- H1 through H31 as marked on the PCB silkscreen
- 4-pin blocks are made by sliding two 2-pin blocks together
- The pin surrounded by a square pad on the PCB is pin 1

### Step 5: Install Resistors
Install in this order, verifying values with a multimeter before soldering:

| Part | Value | Location |
|------|-------|----------|
| R1 | 6.8kΩ | Near Q1 transistor |
| R2 | 10kΩ | Near Q1 transistor |
| R3 | 6.8kΩ | Near LED section |
| R4 | 10kΩ | Near decade counter |
| R5 | 15kΩ | Near oscillator section |
| R8, R9 | 18kΩ each | Upper area |
| R10 | 4.7MΩ | Near decade counter |
| R11 | 10kΩ | Near swap section |
| R12 | 10Ω | Near device socket |

**Tip:** Use a heat sink clip on one leg to hold the component stable while soldering the other.

### Step 6: Install Trimmer Potentiometers
- R6 (1MΩ trimmer) — Swap T1 timing
- R7 (1MΩ trimmer) — Swap T2 timing
- These control the battery swap intervals

### Step 7: Install Capacitors
**Observe polarity — electrolytic capacitors have a marked negative stripe!**

| Part | Value | Notes |
|------|-------|-------|
| C1 | 220nF | Non-polarized, any orientation |
| C2 | 100µF+ 25V | Electrolytic, observe polarity |
| C3 | 100µF+ 25V | Electrolytic, observe polarity |
| C4 | 1000µF+ 25V | Electrolytic, observe polarity |
| C5 | 1000µF+ 25V | Electrolytic, observe polarity |

---

## Phase 3: IC Sockets & Relays

### Step 8: Install DIP-16 Sockets
Install 3 DIP-16 sockets:
- **Socket for U1** (CD4060BE decade counter)
- **Sockets for RLY2 and RLY3** (signal relays)

For the relay sockets, trim pins 3, 5, 7, 10, 12, and 14 (the relay only uses 10 of the 16 holes). Pin 1 is nearest the U-shaped notch.

### Step 9: Install Main Relay (RLY1)
- Solder the 16A power relay (40.61 series) directly to the board
- This is the main battery swap relay

### Step 10: Insert ICs and Relays
- Plug the CD4060BE into its socket (U1) — align the notch
- Plug the two HFD2 signal relays into their trimmed sockets (RLY2, RLY3)

---

## Phase 4: Semiconductors

### Step 11: Install Transistor Q1
- P2N2222A NPN transistor — observe pin orientation (EBC)

### Step 12: Install Diodes
**Observe polarity — the cathode band must match the PCB marking!**
- D1 (1N4007) — main flyback diode
- D2 (1N4001) — protection diode

### Step 13: Install LEDs
**Observe polarity — longer lead is anode (+)**
- LED 1 (Green) — Battery 1 indicator
- LED 2 (Green) — Battery 2 indicator
- LED 3 (Red) — Swap indicator

### Step 14: Install Neon Bulb (U3)
- Safety bypass indicator — no polarity

---

## Phase 5: Test Points & Jumpers

### Step 15: Install All Test Points
Install 2-pin headers at all TP locations (H2-H4, H9, H11, H15-H28). Insert with the shorter leg into the board.

### Step 16: Set Initial Jumper Positions
Place jumper caps on the appropriate test points as per the default configuration. Refer to Table 3 in the technical documentation.

---

## Phase 6: Wiring

### Step 17: Mount External Switches
Mount SW1, SW2, SW3 on a removable plate (perspex recommended) so you can lift the PCB without desoldering.

### Step 18: Wire Switches
- **SW1** (T1/T2): Swap time selection
- **SW2** (Swap On/Off): Enables battery swapping
- **SW3** (HV Swap/Out): HV pulse routing

### Step 19: Wire Batteries
- H1 → Battery 1 (AWG16 wire recommended)
- H5 → Battery 2 (AWG16 wire recommended)
- H6 → Ground (to meters, fuse, main switch)

### Step 20: Wire External Components
- H7/H8 → External load (+ and -)
- H29/H30 → Coils (top and bottom connections)
- H31 → PWM module (Signal In, Supply +, Supply -, Ground)
- H10 → Panel meters

---

## Phase 7: Coils

### Step 21: Wind the Solenoids
Wind 3 solenoid coils on ferrite or mild steel cores:
- Use appropriate gauge wire for desired AT value
- More turns = stronger magnetic field = higher CoP
- Connect coils to H29 (top) and H30 (bottom)

### Step 22: Connect Coils to PCB
- H29-1/H30-1: Coil 1
- H29-2/H30-2: Coil 2
- H29-3/H30-3: Coil 3
- H29-4/H30-4: Spare

---

## Phase 8: Active Device

### Step 23: Install Active Device
Insert your chosen MOSFET/IGBT into the TO-247 device socket (U2):
- STP20N90K5 recommended for first build
- Use jumpers H23-H28 to select correct pin configuration
- The device socket allows easy swapping between different devices

---

## Phase 9: First Power-Up

### Step 24: Pre-Power Checklist
Before applying power, verify:
- [ ] All components in correct positions
- [ ] Capacitor polarities correct
- [ ] Diode orientations correct
- [ ] LED orientations correct
- [ ] No solder bridges between adjacent tracks
- [ ] Continuity check on all connections
- [ ] Battery connections correct polarity

### Step 25: Initial Power Test
1. Connect a 12V power supply (not battery) to H1
2. Turn on main switch
3. LED 1 or LED 2 should illuminate
4. Check supply current (should be in expected range)
5. If nothing happens, proceed to diagnostics in testing guide

### Step 26: Connect PWM Module
1. Connect PWM module to H31
2. Set initial frequency: 100Hz
3. Set duty cycle: 40%
4. Verify square wave output on oscilloscope (if available)

### Step 27: Verify Flyback Pulses
1. With coils connected and PWM running
2. Measure at H14 (HV+ Out) — you should see HV pulses
3. Use the potential divider for safe measurement
4. Expected: 0.5 - 1.7kV depending on active device

---

## Phase 10: Battery Setup & Closed-Loop

### Step 28: Prepare Batteries
1. Fully charge both batteries using their standard charger
2. Discharge 10% of capacity from each
3. Let rest for 60 minutes before IPC

### Step 29: Condition Batteries
- Run 5-7 IPC sessions (LiFePO4) or 10-15 sessions (Pb-acid)
- Battery response improves with conditioning

### Step 30: Achieve Closed-Loop Operation
1. Set battery swapper interval (using R6/R7 trimmers)
2. Enable swapper with SW2
3. Verify LED 1 and LED 2 alternate
4. Connect 5W LED load to H7/H8
5. Monitor — system should self-sustain!

---

## Congratulations!

You have built a working 5W IPC self-charging system. For guidance on testing, calibration, and optimization, see [testing-calibration.md](testing-calibration.md).

Ready to scale up? Visit [IPC.Engineer](https://ipc.engineer) for interactive 3D guides and scaling blueprints from 50W to 10,000W.

---

*Assembly guide maintained by IPC.Engineer — [https://ipc.engineer](https://ipc.engineer)*

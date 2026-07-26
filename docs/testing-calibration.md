# Testing & Calibration Guide

## Overview

Once your PFGen V5A(R) is assembled, this guide walks you through testing, calibrating, and optimizing your system for maximum Coefficient of Performance (CoP).

---

## Diagnostics Checklist

If your system does not work on first power-up, work through these checks:

1. **No LEDs lit**: Check main power connection, fuse, and main switch continuity
2. **No current draw**: Check MOSFET is properly seated in device socket, verify jumper positions H23-H28
3. **No pulses**: Verify PWM module connections at H31, check signal with oscilloscope
4. **Low pulse voltage**: Check coil connections, verify active device is not counterfeit
5. **Erratic swapping**: Check trimmer potentiometer connections R6/R7, verify CD4060 is properly seated

**Your best friend for diagnostics:** A continuity meter to find breaks where there should not be any.

---

## Setting the Battery Swapper

The swapper relay is wired so that it responds to the CD4060 timer output:

1. With power on, turn on the swapper using SW2
2. Set initial T1 to 30-60 seconds
3. Wait for LED1 to illuminate (may take ~2× T1)
4. Once LED1 is on, immediately turn off SW2
5. Select your desired swap interval with SW1 (T1 or T2)
6. Turn SW2 back on — swapper should now operate correctly

---

## Optimizing Operating Parameters

Fine-tune these variables in the following order for best results:

### 1. Pulse Repetition Frequency (PRF)
- Start at 100Hz for LiFePO4 or 50Hz for Pb-acid
- Increment in 5Hz steps, measuring CoP at each
- When improvement appears, narrow to 1Hz increments
- The optimum is very sharp — 1Hz makes a difference!
- Typical ranges: LiFePO4 100-200Hz, Pb-acid 50-100Hz

### 2. Duty Cycle
- Start at 40%
- Adjust downward in 1% increments
- Lower duty = lower current but can maintain energy influx
- Find the minimum duty that still produces measurable results

### 3. Peak Voltage
- Determined by your active device choice
- Higher avalanche rating = higher peak voltage = potentially higher CoP
- Start with STP20N90K5 (~900V), upgrade to STW12N170K5 (~1.7kV) for better results

### 4. Charging Point (%Ah)
- Start at 90% state of charge
- Fully charge battery, then discharge 10% of nominal capacity
- Let battery rest 60 minutes before IPC session

### 5. Charging Time
- Start at 8 minutes for LiFePO4
- The energy influx peaks early then plateaus
- Longer is not always better — find the peak influx point

### 6. Coil Load Voltage
- Measure under load between H29 (positive) and ground
- Target approximately 11.75V
- Adjust power supply as needed

---

## Measuring CoP

### Test Protocol
1. Fully charge battery with mains charger
2. Discharge to target %Ah (e.g., 90%)
3. Rest 60 minutes
4. Run IPC for set charging time
5. Measure: supply voltage, supply current, coil voltage, charging time
6. Discharge battery and measure energy output
7. Calculate: CoP = Energy Out / Energy In

### Data Recording
Use the Data Processing Template spreadsheet for consistent record-keeping and automatic CoP calculations.

---

## Closed-Loop Testing

Once single-battery CoP is optimized:

1. Condition second battery (5-7 sessions for LiFePO4)
2. Set swap interval to match charging time
3. Enable swapper
4. Monitor voltage of both batteries over multiple swap cycles
5. Add external load (start with 1W, increase to 5W)
6. System should maintain or increase battery voltages while powering load

---

*Testing guide maintained by IPC.Engineer — [https://ipc.engineer](https://ipc.engineer)*

# CTA-MTL-Battery-Data
Experimental dataset for electro-thermal characterization of 18650 lithium-ion batteries under multiple discharge conditions.
# CTA-MTL Battery Dataset

This dataset was collected using a custom-built experimental platform to evaluate the electro-thermal behavior of lithium-ion batteries (LIBs) under diverse operating conditions. It supports research on battery modeling, state estimation, and multi-task learning frameworks.

## Experimental Setup
The experimental platform consists of:
- **Battery tester**: Neware CT-8016-5V30A-NTA (16 channels)
- **Temperature chamber**: XF/GDW-500L
- **Host computer**: Windows 7.0, Intel Core i5-1235U @ 4.40 GHz
- **Battery type**: DMEGC INR 18650, 2.6 Ah rated capacity
- **Thermocouples**: K-type (–30 °C to 120 °C, ±1 °C accuracy, 0.1 °C resolution)
- **Sampling interval**: 10 seconds

## Dataset Description
- **Battery cells**: Four DMEGC INR 18650 cells
- **Temperature sensing**: Thermocouples attached to mid-surface; under moderate discharge rates (≤2.3 C), mid-surface ≈ core temperature with <2–4 °C deviation.
- **Measurements recorded**: Voltage (V), current (A), temperature (°C), and time (s).

## Discharge Scenarios
1. **OCV Test** — 1/20C current profile.
2. **Constant-current discharges** — 0.5C, 1C, and 2C.
3. **Pulse discharge** — alternating 10-min 1C discharge & 20-min rest.
4. **Random discharge** — 50 full cycles; current uniformly sampled from 0–6 A, held 120 s per step, generated via MATLAB 2023a.

Charging was performed using the **CC–CV protocol**:
- Constant-current: 1/2C until terminal voltage reached 4.2 V.
- Constant-voltage: continued until current dropped below 1/20C.
- 30-min rest before switching between charge/discharge phases.

## File Structure

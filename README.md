# 🔋 Li-ion Battery Electro-Thermal Dataset

This repository provides an **experimental electro-thermal dataset** of **18650 DMEGC INR Li-ion batteries**, collected under diverse operating conditions using a **custom-built testing platform**.  
It is intended for research on **battery modeling**, **state estimation**, and **electro-thermal coupling analysis**.

---

## 1. Experimental Setup

| **Component** | **Specification** |
|---|---|
| **Battery Type** | DMEGC INR 18650 (Nominal Capacity: 2.6 Ah) |
| **Battery Count** | 4 cells tested independently |
| **Testing System** | Neware CT-8016-5V30A-NTA (16 channels) |
| **Temperature Chamber** | XF/GDW-500L |
| **Thermocouples** | K-type, range: −30 °C to 120 °C, accuracy: ±1 °C |
| **Host Computer** | Windows 7.0, Intel Core i5-1235U @ 4.40 GHz |
| **Ambient Temperature** | 25 °C |
| **Sampling Interval** | 10 s |

> **Note:** Thermocouples were attached to the **mid-surface** of each cell. Under moderate discharge rates (≤ ~2.3 C) and 25 °C ambient, surface measurements closely track internal temperature, making them a practical proxy for core temperature in this dataset.

---

## 2. Dataset Description

Each `.mat` file corresponds to **one battery**, containing multiple experimental scenarios.

### 2.1 File Overview

| **File Name** | **Battery** | **Size (approx.)** | **Description** |
|---|---:|---:|---|
| `Exp25_R1.mat` | Cell #1 | 368 KB | Experimental data for battery R1 |
| `Exp25_R2.mat` | Cell #2 | 371 KB | Experimental data for battery R2 |
| `Exp25_R3.mat` | Cell #3 | 373 KB | Experimental data for battery R3 |
| `Exp25_R4.mat` | Cell #4 | 368 KB | Experimental data for battery R4 |

### 2.2 Data Structures in Each File

| **Variable** | **Description** | **Scenario** | **Unit** |
|---|---|---|---|
| `rw_data` | Random current discharge | 50 random cycles, current uniformly sampled 0–6 A, step 120 s | A, V, °C |
| `ocv_data` | Open-circuit voltage test | Discharge at 1/20 C | V |
| `ref_data` | Constant-current discharge | 1 C discharge | A, V, °C |
| `Rt_c_2_data` | Constant-current discharge | 0.5 C discharge | A, V, °C |
| `Rt_cx2_data` | Constant-current discharge | 2 C discharge | A, V, °C |
| `pulse_data` | Pulse test | 10 min 1 C discharge + 20 min rest (repeating) | A, V, °C |

---

## 3. Experimental Protocols

- **OCV test:** 1/20 C discharge; used to identify the equilibrium OCV–SOC relation.  
- **Constant-current (CC) discharges:** 0.5 C / 1 C / 2 C to cut-off voltage.  
- **Pulse test:** 10 min at 1 C followed by 20 min rest, repeated until cut-off.  
- **Random profiles:** 50 cycles per battery; current steps drawn uniformly in [0, 6] A with 120 s duration; generated offline (MATLAB 2023a).  
- **Charging (CC–CV):** 0.5 C to 4.2 V, then CV at 4.2 V until current < 1/20 C; rest 30 min before the next discharge.

---

## 4. File Organization

```
LIB_Electrothermal_Dataset/
├── Exp25_R1.mat    # Battery R1 data (rw_data, ocv_data, ref_data, etc.)
├── Exp25_R2.mat    # Battery R2 data (same structure as R1)
├── Exp25_R3.mat    # Battery R3 data (same structure as R1)
├── Exp25_R4.mat    # Battery R4 data (same structure as R1)
└── README.md       # Dataset documentation

Inside each .mat file:
    rw_data     → 50 cycles of random current profiles (10 s sampling)
    ocv_data    → Open-circuit voltage test
    ref_data    → 1 C discharge reference test
    Rt_c_2_data → 0.5 C discharge test
    Rt_cx2_data → 2 C discharge test
    pulse_data  → Pulse response test
```

---

## 5. Usage Example

```matlab
% Load example dataset
load('Exp25_R1.mat');

% Access one random-discharge cycle
t  = rw_data(1).time;        % Time vector (s)
i  = rw_data(1).current;     % Current (A)
v  = rw_data(1).voltage;     % Voltage (V)
T  = rw_data(1).temperature; % Surface temperature (°C)

% Plot current profile
figure;
plot(t, i, 'LineWidth', 1.5);
xlabel('Time (s)'); ylabel('Current (A)');
title('Random Discharge Profile - Battery R1');
grid on;
```

---

## 6. Citation

If you use this dataset in your research, please cite:

> **AI-Enhanced Digital Twin Modeling of Cell-Level Lithium-Ion Batteries via Cross-Task Attention-Based Multi-Task Learning**  
> L. Wang *et al.*  
> *IEEE Transactions on Industrial Informatics (TII)*, accept, 2025.

**BibTeX**
```bibtex
@article{Wang2025TII,
  title   = {AI-Enhanced Digital Twin Modeling of Cell-Level Lithium-Ion Batteries via Cross-Task Attention-Based Multi-Task Learning},
  author  = {Lei Wang and Others},
  journal = {IEEE Transactions on Industrial Informatics},
  year    = {2025},
  note    = {Accept}
}
```

---

## 7. License

This dataset is released under the **MIT License**.  
You are free to **use, modify, and distribute** the data for academic and commercial purposes, provided proper attribution is given.

---

## 8. Contact

**Lei Wang**  
Ph.D., Wuhan University  
Postdoctoral Fellow, Oklahoma State University 
📧 Email: [leiwang9305@whu.edu.cn](mailto:leiwang9305@whu.edu.cn)

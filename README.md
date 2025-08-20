# Li-ion Battery Electro-Thermal Dataset

This repository provides an experimental electro-thermal dataset of **18650 DMEGC INR Li-ion batteries** collected under diverse operating conditions. The dataset was generated using a custom-built testing platform and is intended for research in battery modeling, state estimation, and electro-thermal coupling analysis.

---

## **1. Experimental Setup**

The experiments were conducted using a controlled lithium-ion battery testing platform. The setup is shown in Fig. 2 of our paper and summarized below:

| **Component**          | **Specification**                           |
|-----------------------|-------------------------------------------|
| Battery Type         | DMEGC INR 18650 (Nominal Capacity: 2.6 Ah) |
| Battery Count       | 4 cells tested independently |
| Battery Testing System | Neware CT-8016-5V30A-NTA (16 channels) |
| Temperature Chamber | XF/GDW-500L |
| Thermocouples | K-type, range: –30 °C to 120 °C, accuracy: ±1 °C |
| Host Computer | Windows 7.0, Intel Core i5-1235U @ 4.40 GHz |
| Ambient Temperature | 25 °C |
| Sampling Interval | 10 seconds |

**Note:** Thermocouples were attached to the mid-surface of the battery. Prior studies [26,27] demonstrate that the mid-surface temperature deviates less than **2–4 °C** from the core temperature under discharge rates ≤ 2.3 C, so surface temperature can be used as a practical approximation.

---

## **2. Dataset Description**

Each `.mat` file corresponds to a single battery, containing multiple experimental scenarios.

### **2.1 File Overview**

| **File Name**    | **Battery** | **Size** | **Description** |
|-----------------|-------------|----------|------------------|
| `Exp25_R1.mat` | Cell #1     | ~368 KB  | Experimental data for battery R1 |
| `Exp25_R2.mat` | Cell #2     | ~371 KB  | Experimental data for battery R2 |
| `Exp25_R3.mat` | Cell #3     | ~373 KB  | Experimental data for battery R3 |
| `Exp25_R4.mat` | Cell #4     | ~368 KB  | Experimental data for battery R4 |

### **2.2 Data Structures in Each File**

| **Variable**    | **Description** | **Scenario** | **Unit** |
|-----------------|------------------|-------------|----------|
| `rw_data`      | Random current discharge data | 50 random cycles, uniformly sampled current from 0 A to 6 A | A, V, °C |
| `ocv_data`     | Open-circuit voltage test | Discharge at 1/20C | V |
| `ref_data`     | Constant-current discharge test | 1C discharge | A, V, °C |
| `Rt_c_2_data`  | Constant-current discharge test | 0.5C discharge | A, V, °C |
| `Rt_cx2_data`  | Constant-current discharge test | 2C discharge | A, V, °C |
| `pulse_data`   | Pulse discharge test | Alternating 10 min 1C discharge + 20 min rest | A, V, °C |

---

## **3. Experimental Protocols**

1) **Open-Circuit Voltage (OCV) Test**  
   - Discharge current: 1/20 C  
   - Used for identifying equilibrium voltage–SOC relationship.

2) **Constant-Current Discharge Tests**  
   - Three discharge rates: **0.5C**, **1C**, and **2C**  
   - Termination condition: Cut-off voltage reached.

3) **Pulse Discharge Test**  
   - Cyclic sequence: 10 min 1C discharge → 20 min rest → repeat.  

4) **Random Current Discharge Tests**  
   - 50 random cycles per battery  
   - Current uniformly sampled from 0 A to 6 A  
   - Step duration: 120 s  
   - Generated using **MATLAB 2023a**.

5) **Charging Protocol**  
   - **CC–CV** (constant current–constant voltage) method:  
     - Charge at 0.5C until **4.2 V**  
     - Switch to constant voltage until current < 1/20 C  
     - Rest for 30 min before next discharge.

---

## **4. File Organization**

LIB_Electrothermal_Dataset/
│── Exp25_R1.mat # Battery R1 data
│── Exp25_R2.mat # Battery R2 data
│── Exp25_R3.mat # Battery R3 data
│── Exp25_R4.mat # Battery R4 data
└── README.md # Dataset documentation


---

## **5. How to Use**

```matlab
% Load example dataset
load('Exp25_R1.mat');

% Access random discharge cycles
time = rw_data(1).time;     % Time vector
current = rw_data(1).current;
voltage = rw_data(1).voltage;
temperature = rw_data(1).temperature;

plot(time, current);
xlabel('Time (s)');
ylabel('Current (A)');
title('Random Discharge Profile - Battery R1');

## 6. Citation

If you use this dataset in your research or publications, please cite the following paper:

> **AI-Enhanced Digital Twin Modeling of Cell-Level Lithium-Ion Batteries via Cross-Task Attention-Based Multi-Task Learning**  
> L. Wang, et al.  
> *IEEE Transactions on Industrial Informatics (TII)*, under review, 2025.

### BibTeX

```bibtex
@article{Wang2025TII,
  title={AI-Enhanced Digital Twin Modeling of Cell-Level Lithium-Ion Batteries via Cross-Task Attention-Based Multi-Task Learning},
  author={Lei Wang and Others},
  journal={IEEE Transactions on Industrial Informatics},
  year={2025},
  note={Under Review}
}

## 7. License

This dataset is released under the **MIT License**.  
You are free to **use, modify, and distribute** the data for both academic and commercial purposes, **provided proper attribution is given**.

---

## 8. Contact

For questions, feedback, or collaboration opportunities, please contact:

**Lei Wang**  
Postdoctoral Researcher  
Oklahoma State University  
📧 Email: [leiwang9305@whu.edu.cn](mailto:leiwang9305@whu.edu.cn)


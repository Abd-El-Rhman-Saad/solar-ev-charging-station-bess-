# ☀️ Solar-Powered EV Charging Station integrated with Battery Energy Storage System (BESS)

![MATLAB/Simulink](https://img.shields.io/badge/MATLAB-Simulink-blue?logo=mathworks)
![Altium Designer](https://img.shields.io/badge/Altium-Designer-orange)
![Control Systems](https://img.shields.io/badge/Control-Closed_Loop-success)
![Power Electronics](https://img.shields.io/badge/Domain-Power_Electronics-red)

## 📌 Executive Summary
This repository contains the complete engineering design, software simulation models, and hardware fabrication files for a **Standalone Solar-Powered Electric Vehicle (EV) Charging Station**. 

As global adoption of Electric Vehicles accelerates, the demand on the traditional power grid intensifies. This project offers a decentralized, renewable-based solution by harnessing solar energy to charge EVs. To ensure uninterrupted charging and grid independence, a **Battery Energy Storage System (BESS)** is integrated to store excess solar power and supply it during nighttime or cloudy conditions.

The project bridges the gap between deep mathematical modeling (state-space averaging), advanced algorithmic control (Global MPPT), and physical hardware prototyping (PCB design).

---

## 🏗️ System Architecture & Power Flow

The system operates around a stabilized **600V DC-Link**, acting as the main energy hub where power generation, storage, and consumption intersect.

1. **Power Generation:** Photovoltaic (PV) arrays capture solar energy.
2. **First Power Stage (Step-Up):** An Interleaved Boost Converter extracts maximum power from the PV and steps up the voltage to the 600V DC-Link.
3. **Power Management (Storage):** A Battery Energy Storage System (BESS) connects to the DC-Link via a Two-Quadrant (Bidirectional) Chopper, seamlessly switching between charging and discharging to maintain DC-Link stability.
4. **Power Consumption (EV Load):** A Buck Converter steps down the 600V DC-Link to the specific voltage required to safely charge the EV battery.

---

## 🚀 Key Technical Highlights & Modules

### 1. PV Array & Advanced MPPT (`1_PV_Modeling_and_MPPT/`)
Standard Maximum Power Point Tracking (MPPT) algorithms fail under **Partial Shading Conditions (PSC)**, getting trapped in Local Maximum Power Points (LMPP). 
* **Global MPPT (Forced Sweep):** We implemented an advanced Global Scanning algorithm that sweeps the entire P-V curve to locate the absolute Global Maximum Power Point (GMPP), significantly increasing energy yield under uneven shading.
* **Mathematical Modeling:** Includes I-V and P-V characteristic plotting scripts based on the single-diode model.

### 2. Interleaved Boost Converter (`2_Interleaved_Boost_Converter/`)
To interface the PV array with the 600V DC-Link, a standard boost converter would suffer from massive inductor current ripple and thermal stress.
* **Interleaving Technique:** By paralleling two boost phases shifted by 180 degrees, we dramatically reduced the input current ripple, extended the lifespan of the PV panels, and reduced the required inductor sizing.
* **Closed-Loop Control:** Implemented decoupled PI controllers to regulate the output voltage while perfectly tracking the MPPT reference current.

### 3. BESS & Bidirectional Power Control (`3_BESS_and_2Q_Chopper/`)
The brain of the system's energy management. The BESS ensures the DC-Link remains exactly at 600V regardless of solar fluctuations or EV load demands.
* **Two-Quadrant Chopper:** A bidirectional DC-DC converter capable of power flow in both directions.
* **Dual-Loop Control:** A cascaded control architecture featuring an outer Voltage PI loop (maintaining 600V) and an inner Current PI loop (managing battery charge/discharge rates safely).

### 4. EV Buck Charger (`4_EV_Buck_Charger/`)
The final power stage delivering energy to the vehicle.
* **Hardware Validation Model:** Currently contains the open-loop models used to validate the physical hardware prototype components, switching logic, and parasitic losses.
* *(Future Scope)*: Integration of Constant Current / Constant Voltage (CC/CV) charging profiles for lithium-ion battery safety.

### 5. Hardware & PCB Fabrication (`5_Hardware_and_PCB_Design/`)
Moving from software to silicon. This directory contains the Electronic Design Automation (EDA) files designed in **Altium Designer**.
* **Industrial Design Standards:** The PCBs for the converters feature massive polygon pours for high-current paths to minimize Equivalent Series Resistance (ESR).
* **Signal Integrity & Safety:** Implemented strict creepage/clearance constraints for high-voltage isolation, gate driver separation, and Star Grounding techniques to protect the MCU from high-frequency switching noise.

---

## 📘 Full Project Documentation

To keep the repository lightweight, the heavy theoretical documentation and presentation files are hosted in the **GitHub Releases** section. 

👉 **[Download the Graduation Project Book & Presentation Here](../../releases/latest)**

*   **The Thesis Book** contains all state-space derivations, transfer functions, hardware sizing calculations (Inductors, Capacitors, IGBTs), and efficiency analysis.
*   **The Presentation** offers a high-level visual summary of the project's achievements and results.

---

## 💻 How to Use This Repository

1. **Prerequisites:** You will need **MATLAB/Simulink** (with Simscape Electrical) for the simulation files, and **Altium Designer** to view the PCB files.
2. **Navigation:** Each folder is self-contained with its own specific `README.md` explaining the internal files.
3. **Execution:** Open any `.slx` file in the sub-directories. Ensure you run any associated initialization scripts (e.g., `.m` files containing workspace variables) before running the simulation to load the necessary component values and PI gains.

---

## 👥 Acknowledgments
This project was developed as a Bachelor's Degree Graduation Project at the **Electrical Power and Machines Department, Faculty of Engineering, Alexandria University (Class of 2026)**. 

A special thanks to my esteemed teammates and academic supervisors for their dedication and collaborative effort in making this comprehensive engineering system a reality.

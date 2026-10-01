# 🛠️ Hardware Prototyping & PCB Design

This directory contains the Electronic Design Automation (EDA) files used to transition the simulated power converters into physical hardware prototypes. All designs were created and routed using **Altium Designer**[cite: 45].

## 📂 Directory Structure & Files

The project contains complete design packages including Schematic Documents (`.SchDoc`), PCB Layouts (`.PcbDoc`), Engineering Change Order logs (ECO)[cite: 45], and manufacturing files:

*   **Schematics (`.SchDoc`):** Detailed circuit designs including power stage components (IGBTs, MOSFETs, Inductors), gate driver isolation circuits, voltage/current sensing networks, and the microcontroller interface[cite: 45].
*   **PCB Layouts (`.PcbDoc`):** The physical board routing files[cite: 45].
*   **Manufacturing Files (CAMtastic / Gerbers):** Exported CAM files ready for bare-board fabrication[cite: 45].

## ⚡ Power Electronics Design Considerations

Designing PCBs for power electronics requires strict adherence to safety and performance guidelines. The layouts in this directory were routed with the following engineering principles:
1.  **High-Current Paths:** Utilization of massive polygon pours instead of standard traces for high-current nodes to minimize Equivalent Series Resistance (ESR) and prevent thermal hotspots.
2.  **High-Voltage Isolation:** Maintaining adequate clearance and creepage distances between the high-voltage DC link (up to 600V) and the low-voltage control circuitry to prevent arcing and ensure safety.
3.  **Grounding Strategy:** Implementation of strict separation between the Power Ground and Signal/Control Ground (Star Grounding) to prevent high-frequency switching noise from disrupting the sensitive analog measurements and microcontroller logic.

---
*Note: These hardware files represent the physical prototypes utilized to validate the MATLAB/Simulink closed-loop control models found in the other directories.*

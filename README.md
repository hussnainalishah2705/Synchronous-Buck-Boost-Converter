# Synchronous-Buck-Boost-Converter
A Synchronous 4 Switch DC to DC Buck-Boost converter Simulated in Proteus.

A bidirectional, four-switch buck-boost DC-DC converter circuit designed and simulated using Proteus. This topology is capable of both stepping up (boosting) and stepping down (bucking) an input voltage depending on the switching states of the MOSFETs.

## Circuit Schematic Overview

### Key Specifications
* **Input Voltage (VSOURCE):** 5V DC
* **Inductor (L3):** 33µH
* **Output Filtering (C12, C3):** Dual 470µF capacitors in parallel
* **MOSFTE:** IRLZ44N x4 as Q1, Q2, Q3 & Q4
* **Gate Drivers:** IR2104 Half-Bridge Drivers (with integrated dead-time control) which is connected with +12V VCC.
* **Bootstrap Circuitry:** 0.1µF capacitors and fast-recovery diodes for high-side floating gate drive
* **Pulse Voltage Source:** We've used pulse voltage source as V3 & V4 for MOSFET gate switching which will be generating square waves of 5V. 

---

## Operating Modes

This circuit is divided into two operational halves, controlled via independent PWM pulse generators (V3 & V4):

### 1. Boost Mode (Step-Up)
* **Control:** Q1 is kept constantly ON, Q2 is kept constantly OFF, Q3 is off, and Q4 is switching (PWM).
* **Result:** The circuit operates as a boost converter, stepping up the 5V input to a higher voltage at the output load.
* 
### 2. Buck Mode (Step-Down)
* **Control:** Q1 is switching (PWM), Q2 is off, Q3 is kept constantly ON, and Q4 is kept constantly OFF.
* **Result:** The circuit acts as a standard buck converter, reducing the voltage across the output capacitors (C12, C3).

---

## Component Selection & Design Parameters

* **IR2104 Gate Drivers:** Used to drive the high-side MOSFETs (Q1, Q3) and low-side MOSFETs (Q2, Q4). The IR2104 naturally prevents shoot-through by ensuring both outputs are never high at the same time.
* **Gate Resistors:** 47Ω resistors are placed at the IN pins to damp high-frequency ringing and limit logic-level drive currents.
* **Output Capacitors:** Dual parallel 470µF capacitors are utilized to achieve low Equivalent Series Resistance (ESR) and minimize output voltage ripple.

---

## How to Run the Simulation

1. Clone or download this repository.
2. Open the `.pdsprj` file using **Proteus 8.x** or higher.
3. Press the **Play** button in the bottom left corner of Proteus to run the interactive transient simulation.
4. Open the digital oscilloscope tool in Proteus to observe the gate drive signals (HO, LO) and output voltage stabilization.

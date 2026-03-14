![Designed in Altium](https://img.shields.io/badge/Designed%20in-Altium%20Designer-005A9C?style=for-the-badge&logo=altiumdesigner&logoColor=white)
![Status Prototype](https://img.shields.io/badge/Status-Prototype-orange?style=for-the-badge)
![Hardware Open Source](https://img.shields.io/badge/Hardware-Open%20Source-success?style=for-the-badge)

# LPG & Gasoline Injector Pulse Generator / Tester

A professional PCB project for an injector driver designed to test and clean LPG (Liquefied Petroleum Gas) and gasoline fuel injectors. This device generates pulses to open injectors, making it an essential tool for ultrasonic cleaning baths or bench testing.

![3D ISO View](img/PCB_ISO.png)

## 📋 Project Overview

This project is built around the robust **NE555 timer** and the high-performance **IRFZ44N MOSFET**. The PCB is engineered specifically to handle high current spikes typical of low-impedance injector coils.

It allows the user to simulate engine operation by driving the injectors, enabling effective cleaning of internal components when submerged in ultrasonic baths.

### Key Features
* **High Current Design:** Powered by an **IRFZ44N** TO-220 MOSFET, capable of handling significant inductive loads.
* **Thermal Management:** Dedicated Keep-Out Zone and footprint for a substantial heatsink (e.g., Fischer Elektronik SK 09 20 SA) for continuous operation.
* **Robust Connectivity:** Industrial-grade 5.08mm screw terminals (ARK) for secure power and injector connections.
* **Safety:** Integrated fuse holder footprint for circuit protection.

---

## 📸 Design Gallery

### Top Layout
Clean component placement optimized for airflow and easy assembly.
![Top View](img/PCB_TOP.png)

### Bottom Layout
![Bottom View](img/PCB_BOT.png)

### Schematic Diagram
Based on the NE555 astable multivibrator configuration with adjustable frequency/duty cycle.
![Schematic](img/SCHEMATIC.png)

---

## ⚙️ Technical Specifications

| Parameter | Value |
| :--- | :--- |
| **Dimensions** | ~77mm x 87mm |
| **Layers** | 2 |
| **Material** | FR-4 Standard |
| **Thickness** | 1.6 mm |
| **Copper Weight** | 1 oz (35µm) - *Tinning recommended* |
| **Power Input** | 12V DC (Automotive standard) |
| **Mounting** | 4x M3 Mounting Holes |

---

## 🛠️ Bill of Materials (Key Components)

| Designator | Component | Description |
| :--- | :--- | :--- |
| **Q1** | **IRFZ44N** | N-Channel Power MOSFET, TO-220 |
| **U1** | **NE555P** | Precision Timer DIP-8 |
| **Heatsink** | SK 09 20 SA | Fischer Elektronik (or compatible TO-220 vertical heatsink) |
| **J1 - J4** | ARK 5.08mm | 2-pin Screw Terminal Blocks |
| **VR1** | Potentiometer | For Frequency/Duty Cycle adjustment |
| **F1** | Fuse Holder | Automotive blade fuse holder |

---

## 🚀 Manufacturing (Gerber Files)

Production-ready files are available in this repository. The project has been validated for manufacturing with standard low-cost PCB houses (JLCPCB, PCBWay).

**Files location:**
* `/Project Outputs for pulse_generator` contains the raw output.
* Check the **Releases** section for the zipped `Pulse_generator_gerber_files.zip`.

**Recommended Ordering Settings:**
* **Layers:** 2
* **Thickness:** 1.6mm
* **Solder Mask:** Green (or preferred color)
* **Surface Finish:** HASL (Lead or Lead-Free)
* **Remove Order Number:** Specify "Yes" if you want a clean look.

---

## 📖 Usage Guide

### 1. Initial Setup & Dry Test
**Always perform a dry test before submerging injectors in liquid.**
1. Connect to a **12V DC** power supply (capable of delivering at least 5A-10A).
2. Set the frequency switch to **1 Hz DEF**.
3. Turn the **PWM (Duty Cycle)** knob to the **absolute minimum** (fully counter-clockwise).
4. Start the **Master Timer**.
5. **Verification:** Use a mechanic's stethoscope or touch the injector. You should hear a clear, metallic "click". 
   * *If silent:* Slowly increase PWM until the internal needle starts moving. **Stop there.**

### 2. Frequency Modes Explained
The PCB labels correspond to optimized cleaning stages:

| PCB Label | Real Frequency (Measured) | Application |
| :--- | :--- | :--- |
| **1 Hz DEF** | **~1.8 Hz** | Initial "shock" soaking. Best for loosening heavy, gummy deposits. |
| **25 Hz DEF** | **~33 Hz** | **Standard Cleaning.** Simulates engine idle/load. Ideal for most scenarios. |
| **60 Hz DEF** | **~70 Hz** | Intensive flushing. Maximizes fluid exchange inside the injector. |

---

## ⚠️ Special Note for Low-Z Injectors (1.8 Ω - 3 Ω)

Low-resistance injectors (common in LPG rails) act like heaters when driven with a constant 12V signal. 

> [!CAUTION]
> **OVERHEATING RISK:** Running 1.8 Ω coils without a current-limiting resistor results in ~6.6A peaks. 
> * **PWM Control:** Use the **lowest possible PWM setting** that maintains mechanical clicking. 
> * **Liquid Level:** Immerse only the metal nozzle and rail body. **NEVER** let fluid touch the electrical plugs.
> * **Monitoring:** Touch the rail every 60 seconds. If it exceeds **50°C (hot to the touch)**, stop immediately.

---

## 🧼 Cleaning & Maintenance

1. **Submerge:** Place the nozzles in the ultrasonic bath (keeping connectors dry).
2. **Cycle:** Run the preferred frequency mode for 3-5 minutes.
3. **Dry:** After cleaning, blow out any remaining fluid with compressed air.
4. **Protect:** Flush the internal mechanism with **WD-40** or light machine oil immediately to prevent rust on internal springs.

---

## ⚠️ Disclaimer

**Use at your own risk.** This device controls fuel injectors which operate with flammable liquids and high currents.
* Always ensure proper ventilation when working with fuel.
* Ensure the MOSFET is properly isolated if the heatsink is not grounded.
* The authors are not responsible for any damage to injectors, power supplies, or other equipment resulting from the use of this project.

---

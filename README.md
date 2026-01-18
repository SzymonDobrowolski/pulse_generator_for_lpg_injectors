# LPG Injector Pulse Generator & Cleaner

![Project Status](https://img.shields.io/badge/Status-Prototype-yellow)
![EDA Software](https://img.shields.io/badge/Designed_in-Altium_Designer-blue)

## 📖 Overview
This project is a standalone, high-current pulse generator designed specifically for **cleaning, testing, and diagnosing low-impedance LPG injectors** (e.g., Tartarini, Valtek, Magic Jet). 

Unlike simple "clickers," this device features full adjustability of **Frequency**, **Pulse Width (PWM)**, and **Operation Time**, allowing for safe and effective cleaning without overheating the injector coils.

## 🚀 Key Features

* **⚡ Master-Slave Architecture:** Based on two NE555 timers for reliability and analog precision.
* **⏱️ Automatic Safety Timer (Master):** Adjustable operation time (approx. 3 to 10 minutes). The device automatically cuts off power after the set time to prevent unattended operation.
* **🎛️ Adjustable Duty Cycle (PWM):** Precise control over the injector opening time. Allows you to set the "power" of the pulse to prevent coil overheating while maintaining effective cleaning.
* **🔄 Variable Frequency Ranges:** Switchable frequency modes to suit different tasks:
    * **Low Frequency (~1 Hz):** For listening tests and checking for stuck pintles.
    * **High Frequency (~25-50 Hz):** For dynamic cleaning and flow simulation.
* **🛡️ Robust Protection:**
    * Flyback diodes (Schottky) on each channel to protect against high-voltage spikes.
    * High-current MOSFET design capable of driving **4 injectors** simultaneously (parallel connection).
    * Fuse protection on the main power input.

## ⚙️ Technical Specifications

| Parameter | Value / Range |
| :--- | :--- |
| **Input Voltage** | 12V - 14.4V DC (Car Battery or High-Current PSU) |
| **Target Injectors** | Low Impedance (1Ω - 3Ω), e.g., Tartarini, Valtek |
| **Current Capacity** | up to 20A Peak (4 injectors) |
| **Timer Range** | Adjustable ~3 min – 10 min |
| **Frequency** | Selectable ranges (approx. 1Hz / 50Hz) |
| **PWM Range** | Adjustable ~5% – 95% |

## 🧠 Circuit Concept

The device operates on a **Master-Slave** principle using two NE555 ICs:

1.  **U2 (Master - Monostable Mode):**
    * Activated by a tactile switch.
    * Controls the `RESET` pin of the second timer.
    * Determines how long the cleaning process lasts.
2.  **U1 (Slave - Astable PWM Mode):**
    * Generates the actual pulses driving the MOSFET.
    * Uses a specialized diode-steering circuit to allow fixed-frequency PWM adjustment.
    * Capacitor switching allows for jumping between frequency ranges (Test/Clean modes).

## 🛠️ Hardware & PCB

The PCB was designed in **Altium Designer** with a focus on high-current handling.

* **Power Paths:** Wide traces and polygon pours on 12V and GND lines to handle the combined current of 4 coils.
* **Thermal Management:** Layout includes space for a heatsink on the main MOSFET (IRF3205/IRFZ44N).
* **Components:** Uses standard THT components for easy assembly by hobbyists.

### BOM (Key Components)
* 2x NE555 Timers
* 1x IRF3205 or IRFZ44N MOSFET
* 4x 1N5822 / SB540 Schottky Diodes (Flyback protection)
* Potentiometers for Time & PWM control
* Passive components (Resistors, Capacitors)

## 📂 Project Structure

* `/Altium` - Source project files (Schematic, PCB).
* `/Gerber` - Production files for PCB manufacturing (JLCPCB/PCBWay ready).
* `/Simulation` - LTspice simulation models used for circuit analysis.
* `/Docs` - Additional diagrams and schematics.

## ⚠️ Safety Disclaimer
**Warning:** This device controls high-current inductive loads and is often used with flammable cleaning fluids (e.g., brake cleaner, gasoline).
* Always work in a well-ventilated area.
* Ensure the power supply has a proper current rating (min. 15A).
* Do not leave the device unattended during operation.
* The author is not responsible for any damage caused by improper use or assembly.

---
*Created by [Twoje Imię/Nick]*

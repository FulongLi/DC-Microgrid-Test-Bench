# Low-Voltage DC Microgrid Test Bench / Hardware & Schematics

![license - CC BY 4.0](https://img.shields.io/badge/license-CC--BY-green)
![language - Electronics](https://img.shields.io/badge/language-Hardware-blue)
![category - power electronics](https://img.shields.io/badge/category-power%20electronics-lightgrey)
![status - archived](https://img.shields.io/badge/status-archived-red)

This repository contains the **hardware design, schematics, and system description** of a **low-voltage DC microgrid experimental bench**.  
The platform was developed for validating control strategies, converter design, and system-level energy management in DC microgrids.

The test bench includes:

- A **DC microgrid backbone**
- Four **bidirectional interface converters** (Boost / Bidirectional Boost)
- **PV emulator**, **battery banks**, and **DC supply** for grid emulation  
- **Electronic load**, resistive loads, and full measurement interface  
- Fully isolated **control + power boards** using TMS320F28335 DSP

The system enables flexible testing of grid-connected and islanded DC microgrids, with realistic renewable/load emulation and accurate current/voltage feedback.

---

## System Overview

The DC microgrid test bench consists of:

- Interface converters  
- PV emulator  
- Battery banks  
- DC power supply (grid emulator)  
- Electronic load  
- Resistive loads  
- Central PC for monitoring and control  

Two operating modes are supported: **Grid-connected mode** and **Islanded mode**.

---

## Hardware Architecture

### 1. Power Board

The power board includes:

- Bidirectional boost converter  
- Current & voltage sensing  
- Gate drivers  
- Differential amplifier signal conditioning  

**Key Components:**
- MOSFET: FDP42AN15A0  
- Current transducer: CASR 6-NP  
- Voltage sensor: LV25-P  
- Gate driver: HCPL-3120  
- Isolated supply: TMA1515S  
- Op-amp: LM224  

---

### 2. Control Board

Includes:

- DSP TMS320F28335  
- TRACO isolated power modules  
- ± supply rails for sensors and drivers  

**Key Components:**
- TRACO TEN 5-4812WI  
- IL1205S  
- IL1215S  
- TMS320F28335 control card  

---

## Distributed Source Connections

The full experimental setup uses **four converters**:

| Converter # | Source | Mode |
|-------------|--------|------|
| 1 | Grid-connected (DC supply) | Bidirectional |
| 2 | Battery Bank A | Bidirectional |
| 3 | Battery Bank B | Bidirectional |
| 4 | PV Emulator | Unidirectional (Boost) |

### Grid Emulation
- DC supply provides grid-side voltage  
- 10 Ω soaking resistor dissipates returned power  

### Battery Storage
- 12 V / 24 Ah batteries × 2 per bank  
- Connected as 24 V input  

### PV Emulator
- 0–40 V  
- Up to 150 W  
- Fully controllable  

**System parameters:**
- Input capacitor: 470 µF  
- Inductor: 240 µH  
- Output capacitor: 470 µF  
- Converter rating: 250 W  
- Topology: Bidirectional Boost  

---

## Repository Structure


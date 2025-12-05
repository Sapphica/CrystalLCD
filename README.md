# Crystal-LCD

_A custom Rainmeter telemetry engine driving a 1920×480 glass LCD with real-time PC stats, overclock info, and FPS._

<div align="center">

![Build](https://img.shields.io/badge/BUILD-PASSING-8A2BE2?style=for-the-badge)
![Platform](https://img.shields.io/badge/PLATFORM-WINDOWS-444444?style=for-the-badge&logo=windows)
![Rainmeter](https://img.shields.io/badge/RAINMETER-CUSTOM_SKIN-9370DB?style=for-the-badge)
![Telemetry](https://img.shields.io/badge/TELEMETRY-HWiNFO-6A5ACD?style=for-the-badge)
![FPS](https://img.shields.io/badge/FPS-MSI_AFTERBURNER-228B22?style=for-the-badge)
![Lua](https://img.shields.io/badge/LUA-SCRIPTING-BA55D3?style=for-the-badge&logo=lua)
![C++](https://img.shields.io/badge/C%2B%2B-PLUGIN_BACKEND-6A5ACD?style=for-the-badge&logo=c%2B%2B)

</div>

---

## 🎥 Demo

<div align="center">
  <img src="https://github.com/Sapphica/Crystal-LCD/blob/main/assets/LCD.gif" alt="Crystal-LCD Telemetry Panel" width="720">
</div>

---

## ⭐ Purpose

Crystal-LCD is a **glass-style telemetry HUD** for a dedicated 1920×480 LCD panel.  
It’s built to sit under the main display and show **everything that actually matters** while gaming or stress-testing:

- ⭐ **AMD star-core tracking**, including real-time core-parking detection and a **gold 3XD indicator** when a V-Cache star core activates  
- CPU clocks, temps, utilization, power, overclock indicator  
- GPU clocks, temps, VRAM usage, PCIe link speed, power draw  
- FPS (live + rolling average) with layout switching at high framerates  
- Pump RPM, radiator temperature (current + max)  
- Per-drive SMART health, lifespan, and temperature  
- System uptime, RAM usage, top CPU process  

All of this is driven through **Rainmeter + HWiNFO + MSI Afterburner + plugins**, wired together by a single `CrystalTelemetry.ini` and `GIF.ini`.

---

## 📝 Notes

- **This skin is tuned for a specific hardware setup and resolution (1920×480).**
- **It can be adapted**, but the intent is very much:
- 
<i>“This is my personal glass telemetry cockpit.”</i>

The `.ini` is intentionally dense: it’s a full subsystem, not a toy widget.

---

## 🧩 Features

### 🔥 CPU Telemetry

- CPU total usage with warning color when > 90%  
- Per-core utilization  
- Active-clock selection logic (detects which CCD is active, x3D vs non-3D)  
- CPU clock reporting  
- CPU voltage  
- CPU package power  
- CPU temperature (current + max)  
- Overclock indicator with gold pulse when the x3D path is active  

### 🎮 GPU Telemetry (GPU 0 + optional GPU 1)

- Core clock  
- Memory clock  
- GPU temps (current + max)  
- PCIe link speed  
- GPU voltage  
- Total power draw  
- VRAM usage (%) and allocated (GB/MB)  
- PCIe + VRAM + voltage combined readout line  

### 🎯 FPS + Performance Behavior

- Live FPS  
- Rolling average  
- Auto layout switching at ≥ 100 FPS  
- Click-to-refresh hotspot  

### 🧠 Memory + System

- RAM used vs total  
- Swap usage  
- System uptime  
- CPU name (registry)  

### 💾 Storage / SMART Telemetry

- Drive Fail / Warning status  
- Drive Life %
- Drive temperature per-drive  

### 💧 Cooling / Loop Monitoring

- Pump RPM  
- Radiator temperature (current + max)  

### 🧨 Top Process View

- Live top CPU process  
- CPU % for that process  

### ⚡ Total Power (Combined)

- GPU + CPU power sum (ready when you enable CPU_Power)  

---

## 🧰 Technology Stack

### 💻 Application Environment

- **Windows + Rainmeter**  
- **HWiNFO**  
- **MSI Afterburner**  
- **AdvancedCPU.dll**  
- **Mini 1920×480 LCD panel**  

### ⚙️ Code & Config

- **Rainmeter `.ini` skin**  
- **Lua** helper scripts  
- **C++ plugin backends** for HWiNFO, MSI, AdvancedCPU  

---

## 📁 Structure (High Level)

```text
Crystal-LCD/
  CrystalTelemetry.ini        # Main Rainmeter skin for the LCD
  @Resources/
    Variables.inc             # Colors, fonts, sizing, shared variables
    Sensors.inc               # HWiNFO / MSI ID mappings (per-machine)
    Images/                   # Backgrounds, reflection overlays, etc.
  assets/
    LCD.gif                   # Demo animation for README

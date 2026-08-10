### System Specifications

| Parameter | Value / Component |
| :--- | :--- |
| **Input Voltage** | $9\text{V AC RMS}$ ($\approx 12.7\text{V}_{\text{peak}}$) |
| **Output Voltage** | $20\text{V DC}$ (Regulated) |
| **Switching Frequency** | $50\text{kHz}$ |
| **Boost Inductor** | $470\mu\text{H}$ |
| **Output Capacitor** | $1000\mu\text{F}$ |
| **Rectifier / Boost Diode** | 1N5819 (Schottky) / UF4004 (Ultra-Fast) |

---

### Simulation Output

![APFC Simulation Waveforms](sim%20output.png)

---

### Simulation Waveforms & Analysis

#### 1. Input Voltage & Current Waveforms (Grid Side)
* **Phase Synchronization**: The input AC current tracks the sinusoidal input AC voltage in phase, confirming low phase shift and high Power Factor ($\text{PF} \approx 1$).
* **Current Shaping & Distortion**: The current loop shapes the waveform into a sinusoid. Small zero-crossing dead zones are observed during polarity switching due to bridge rectifier diode forward voltage drops.
* **Switching Ripple**: High-frequency current ripple is visible along the sinusoidal envelope as a result of the $50\text{kHz}$ switching action across the $470\mu\text{H}$ boost inductor.

#### 2. Output DC Voltage Response
* **Steady-State Regulation**: The outer PI loop maintains a continuous average DC level of $20\text{V}$.
* **Output Ripple**: A $100\text{Hz}$ low-frequency ripple ($\sim 2\text{V}_{\text{p-p}}$) is present, caused by double-line frequency power fluctuations standard in single-phase PFC systems, buffered by the $1000\mu\text{F}$ capacitor.

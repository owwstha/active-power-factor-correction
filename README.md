## Active Power Factor Correction (APFC)

### Overview & Objectives

The primary objective was to design a high-efficiency Active Power Factor Correction stage. Utilizing a PI control loop to modulate PWM signals, the system achieves a Power Factor (PF) > 0.99. Key design priorities included:
* Minimizing THD.
* Regulating the DC bus voltage against AC input fluctuations and sudden load transients.

---

### Technical Details

* **Control Architecture**: A dual-loop PI control system manages the feedback: a outer voltage PI loop stabilizes the DC bus output, while a fast inner current PI loop continuously adjusts the duty cycle of the PWM signal.
* **Power Stage**: A diode bridge rectifier converts the AC line voltage to unsmoothed DC, which is immediately fed into a high-frequency Boost Converter. The switched PWM controls the boost stage to shape the input current into a pure sinusoidal waveform aligned with the AC voltage.

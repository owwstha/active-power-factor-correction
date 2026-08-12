### Mathematical Formulation & Control Design

#### 1. Inductor Current Ripple ($\Delta I_L$)
The worst-case inductor current ripple occurs at a 50% duty cycle ($D = 0.5$):

$$\Delta I_L = \frac{V_o \cdot D \cdot (1 - D)}{L \cdot f_s}$$

Substituting $V_o = 20\text{V}$, $L = 470\mu\text{H}$, and $f_s = 50\text{kHz}$:

$$\Delta I_L = \frac{20\text{V} \times 0.5 \times 0.5}{470\mu\text{H} \times 50\text{kHz}} \approx 0.213\text{A} \quad (213\text{mA})$$

---

#### 2. Output Capacitor Voltage Ripple ($\Delta V_o$)
In single-phase APFC, double-line frequency ($2 f_{\text{line}} = 100\text{Hz}$) causes peak-to-peak voltage ripple on the DC bus:

$$\Delta V_{o,\text{p-p}} = \frac{I_o}{2 \pi f_{\text{line}} \cdot C} = \frac{P_{\text{out}}}{2 \pi f_{\text{line}} \cdot C \cdot V_o}$$

For a nominal load current $I_o \approx 0.6\text{A}$ at $f_{\text{line}} = 50\text{Hz}$ and $C = 1000\mu\text{F}$:

$$\Delta V_{o,\text{p-p}} = \frac{0.6\text{A}}{2 \pi \times 50\text{Hz} \times 1000\mu\text{F}} \approx 1.91\text{V}_{\text{p-p}}$$

---

#### 3. PI Controller Gains

* **Inner Loop (Current Control)**
  * P=1, I=50
  * Fast control loop designed to force inductor current $I_L(t)$ to track the rectified AC voltage reference.
  * **$K_{p,i}$**: High proportional gain to maximize bandwidth and minimize switching ripple phase error.
  * **$K_{i,i}$**: Integral gain to eliminate steady-state current tracking error.

* **Outer Loop (Voltage Control)**
  * P=0.1, I=10
  * Slow control loop regulating the average output DC voltage ($20\text{V}$).
  * **$K_{p,v}$**: Proportional gain tuned for low crossover frequency ($<20\text{Hz}$) to avoid amplifying $100\text{Hz}$ ripple into the current reference.
  * **$K_{i,v}$**: Integral gain ensuring zero steady-state error under varying load conditions.

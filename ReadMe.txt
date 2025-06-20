## 🔧 1. **What is a Single-Phase Half-Wave Uncontrolled Rectifier?**

A **half-wave rectifier** is a circuit that allows **only one half of an AC waveform** to pass through to the load, blocking the other half. It uses **a single diode** in series with the load to achieve this.

This is called **uncontrolled** because it uses a diode (not a thyristor), and therefore **no external control signal** is required.

---

## 🔄 2. **Working Principle**

* **During Positive Half-Cycle** of input AC:

  * Diode becomes **forward-biased**
  * Current flows through the **diode → load → back to source**
  * Output voltage follows the input (less diode drop)

* **During Negative Half-Cycle**:

  * Diode becomes **reverse-biased**
  * No current flows
  * Output voltage = 0

---

## 🧰 3. **Components Required for Simulation in Simulink**

1. **AC Voltage Source**
2. **Diode (Uncontrolled)**
3. **Resistive Load (R)**
4. **Current & Voltage Measurement blocks**
5. **Scope**

---

## 📊 4. **Typical Parameter Values for Simulation**

| Parameter           | Value                     | Notes                          |
| ------------------- | ------------------------- | ------------------------------ |
| AC Supply Voltage   | 230 V RMS (or 325 V peak) | Sinusoidal                     |
| Frequency           | 50 Hz                     | Standard                       |
| Diode               | Ideal or with Vf = 0.7 V  | Use built-in Diode block       |
| Load Resistance (R) | 10 Ω                      | Typical resistive load         |
| Simulation Time     | 0.1 to 0.2 sec            | Enough to view multiple cycles |
| Step Size           | Automatic or 1e-5         | For accurate waveform          |
| Solver              | `ode23tb` or `ode45`      | Recommended for power systems  |

---

## 🔌 5. **Simulink Block Setup**

### AC Source

* Use **Sine Wave block** from "Simulink > Sources"
* Amplitude = 325 (for 230 RMS)
* Frequency = 50 Hz

### Diode

* Use **Diode block** from "Simscape > Foundation > Electrical > Semiconductors"

### Load

* Use **Resistor** block from "Simscape > Foundation > Electrical > Electrical Elements"

### Connect

```
Sine Source (+) ───►│──── R ──── Ground
                   D
Sine Source (-) ────────────────┘
```

### Measurement

* Use **Voltage Sensor** and **Current Sensor**
* Connect to **Scope** for waveform analysis

---

## 📈 6. **Expected Output Waveforms**

### Load Voltage (Vload)

* Positive half-cycle resembles a **clipped sine wave**
* Negative half-cycle is **0 V**

### Load Current (Iload)

* Same shape as Vload (since load is resistive)

---

## 📐 7. **Formulas (Optional for Analysis)**

* **Peak Output Voltage**:
  V_peak= V_m - V_d
  where V_m = Peak AC voltage, V_d = Diode drop

* **Average Output Voltage**:
  V_avg = V_m/pi

* **RMS Output Voltage**:
  V_rms = V_m/2





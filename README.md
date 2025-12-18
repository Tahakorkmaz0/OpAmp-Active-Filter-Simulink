# Op-Amp Adder and Active Band-Pass Filter Design

A signal processing system using operational amplifiers to combine and filter multiple frequency components, designed and simulated in Simulink/Simscape.

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [System Architecture](#system-architecture)
- [Component Specifications](#component-specifications)
- [Simulation Results](#simulation-results)
- [Getting Started](#getting-started)
- [Documentation](#documentation)
- [License](#license)

## 🎯 Project Overview

This project implements an operational amplifier-based signal processing system designed to:

- **Combine** three sinusoidal AC input signals with different frequencies:
  - 0.1 Hz (low frequency)
  - 10 Hz (target frequency)
  - 1000 Hz (high frequency)

- **Extract** the 10 Hz component while suppressing the other frequencies using an active filtering structure

The system is built using the **LM741** operational amplifier model and simulated in MATLAB Simulink/Simscape environment.

## 🔧 System Architecture

The circuit consists of four cascaded stages:

### 1. Inverting Summing Amplifier
Combines the three input signals into a single composite waveform.

### 2. High-Pass Filter (HPF)
- Attenuates the 0.1 Hz low-frequency component
- Cutoff frequency: **f<sub>c,HP</sub> ≈ 1.2 Hz**

### 3. Non-Inverting Amplifier
- Provides isolation between filter stages
- Voltage gain: **1.1** (maintains stable operation)

### 4. Low-Pass Filter (LPF)
- Attenuates the 1000 Hz high-frequency component
- Cutoff frequency: **f<sub>c,LP</sub> ≈ 120 Hz**

### Block Diagram

```
[0.1 Hz]  ──┐
            ├──> [Summing] ──> [HPF] ──> [Amp] ──> [LPF] ──> [10 Hz Output]
[10 Hz]   ──┤    Amplifier    1.2 Hz    x1.1      120 Hz
            │
[1000 Hz] ──┘
```

## 📊 Component Specifications

| Section              | Component      | Value    | Unit |
|---------------------|----------------|----------|------|
| **Op-amp Adder**    | R1, R2, R3, Rf | 10       | kΩ   |
| **High-Pass Filter**| R_HP           | 132.63   | kΩ   |
|                     | C_HP           | 1        | μF   |
| **Low-Pass Filter** | R_LP           | 100      | Ω    |
|                     | L_LP           | 132.3    | mH   |

### Design Equations

**High-Pass Filter:**
```
f_c,HP = 1/(2π × R_HP × C_HP) ≈ 1.2 Hz
```

**Low-Pass Filter:**
```
f_c,LP = R_LP/(2π × L_LP) ≈ 120 Hz
```

## 📈 Simulation Results

The simulation successfully demonstrates the band-pass filtering characteristics:

✅ **Signal Merging:** The summing amplifier correctly combines all input frequencies into a single composite waveform

✅ **Filtering Performance:** 
- The 0.1 Hz component is significantly attenuated by the HPF
- The 1000 Hz component is significantly attenuated by the LPF

✅ **Output Verification:** Cursor measurements indicate a signal period of approximately **0.1 s**, corresponding to the target **10 Hz** frequency

### Key Observations

- The 10 Hz component remains dominant at the output
- Minimal distortion of the target frequency
- Effective suppression of unwanted frequency components

## 🚀 Getting Started

### Prerequisites

- MATLAB R2020b or later
- Simulink
- Simscape Electrical

### Running the Simulation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/opamp-bandpass-filter.git
   cd opamp-bandpass-filter
   ```

2. Open MATLAB and navigate to the project directory

3. Open the Simulink model:
   ```matlab
   open_system('opamp_filter_model.slx')
   ```

4. Run the simulation:
   ```matlab
   sim('opamp_filter_model.slx')
   ```

## 📁 Documentation

Detailed visual analysis and simulation waveforms (Scope outputs) can be found in the `/docs` folder:

- Circuit schematics
- Bode plots
- Time-domain waveforms
- Frequency response analysis

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

- Your Name - Initial work

## 🙏 Acknowledgments

- LM741 Op-Amp datasheet and specifications
- MATLAB/Simulink documentation
- Active filter design references

---

**Note:** This project is for educational purposes and demonstrates fundamental concepts in analog signal processing and active filter design.

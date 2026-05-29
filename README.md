# Melanin Compensated SpO2 Algorithm Core (SiMD)

[![Compliance](https://img.shields.io/badge/Regulatory-IEC_62304_Class_B-blue.svg)](#)
[![Framework](https://img.shields.io/badge/Design-Model--Based_Design-orange.svg)](#)
[![Language](https://img.shields.io/badge/Output-Embedded_C%2B%2B-green.svg)](#)
[![License](https://img.shields.io/badge/License-Proprietary-red.svg)](#)

A pure software, host agnostic signal processing core developed to eliminate systemic skin pigmentation inaccuracies in dual wavelength pulse oximetry systems.

---

## 🔴 The Problem

Standard commercial pulse oximeters measure blood oxygen saturation (SpO2) by analysing how oxygenated and deoxygenated haemoglobin absorb red (660nm) and infrared (940nm) light differently. However, melanin, the pigment determining skin tone, absorbs red light significantly more than infrared light, distorting the optical ratio and causing systematic SpO2 overestimation in darker skinned patients across Fitzpatrick Types IV-VI and the Monk Skin Tone scale.

This causes occult hypoxemia, a clinically dangerous condition where a monitor falsely reads safe blood oxygen levels (≥92%) while true arterial saturation is critically low, leading to delayed treatment decisions, documented in FDA safety communications since 2022.

---

## 🚀 The Solution: Software-Defined Compensation

Rather than requiring multi wavelength hardware redesigns, a pure mathematical compensation engine was developed to optimize existing hardware. By evaluating realtime non-pulsatile optical attenuation, the algorithm dynamically classifies tissue properties and balances optical ratios without modifying any optoelectronic components.

### Architecture Overview

![Simulink Architecture Pipeline](Full_Model.png)

### Core Pipeline (6 Functional Blocks)

![Melanin Compensated SpO₂ Signal Processing Pipeline](SpO2_Core_Pipeline.png)

---

## 📊 Performance Verification & Results

The algorithm was verified using the PTT-PPG dual-wavelength 
dataset (PhysioNet), recorded with a MAX30101 medical-grade 
optical sensor at 500Hz.

![Validation Results](Complete_Algorithm_Results_PTT_PPG.png)

![Validation Results](DUAL-CHANNEL_AC-DC_DECOMPOSITION_PTT_PPG.png)

![Validation Results](Melanin_Index_Analysis_PTT_PPG.png)


### Key Metrics

| Metric | Value | Standard | Status |
|--------|-------|----------|--------|
| **ARMS** | **2.35%** | FDA ≤3.0% | ✅ PASS |
| Precision (σ) | 0.22% | — | Excellent |
| Valid Windows | n=213 | — | Statistically sound |
| PI Quality Gate | 88% valid | — | Working correctly |

Skin-aware correction eliminates dark skin tone bias without 
introducing measurement inaccuracy in light or medium skin tones 
(Fitzpatrick I-VI).

---

## 🛠 Technology Stack

| Component | Detail |
|-----------|--------|
| Design Environment | MATLAB R2023b / Simulink |
| Design Methodology | Model-Based Design (V-Model) |
| Code Output | Production C++ via Embedded Coder |
| Target Architecture | Host-agnostic, inherited sample-time (-1) |
| Regulatory Framework | IEC 62304 Class B SDLC |
| Dataset | PTT-PPG (PhysioNet), MAX30101 sensor |

---

## 📋 Development Status

✅ Requirements specification complete (URS + SRS, 50 requirements)

✅ Full bidirectional traceability (URS → SRS → Design → Verification)

✅ MATLAB algorithm prototyping complete (6 blocks)

✅ Simulink Model-Based Design complete

✅ Production C++ code generation complete (Embedded Coder)

✅ Performance verification complete (ARMS = 2.35%)

🔄 Full DHF documentation in progress

---

## 📁 Repository Contents

This public repository contains verification visuals and 
high level architectural documentation only.

| File | Description |
|------|-------------|
| `Full_Model.png` | Simulink functional module architecture |
| `Complete_Algorithm_Results_PTT_PPG.png` | Validation metrics |
| `DUAL-CHANNEL_AC-DC_DECOMPOSITION_PTT_PPG.png` | Signal decomposition |
| `Melanin_Index_Analysis_PTT_PPG.png` | Tier classification metrics |

> **IP Notice:** Proprietary model logic (`.slx`), calibration 
> parameter scripts (`.m`), correction coefficients, and 
> generated C++ source files are explicitly excluded to 
> safeguard Anyionic Technologies' intellectual property.

---

## 📬 Contact

For technical discussions or collaboration enquiries:

**Ifeanyichukwu Obidike**

Founder, Anyionic Technologies

[LinkedIn](https://www.linkedin.com/in/ifeanyichukwu-obidike-532200199)

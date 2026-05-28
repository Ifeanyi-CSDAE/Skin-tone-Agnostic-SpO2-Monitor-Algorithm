# Melanin-Compensated SpO2 Algorithm Core (SiMD)

[![Compliance](https://img.shields.io/badge/Regulatory-IEC_62304_Class_B-blue.svg)]
[![Framework](https://img.shields.io/badge/Design-Model--Based_Design-orange.svg)]
[![Language](https://img.shields.io/badge/Output-Embedded_C%2B%2B-green.svg)]
[![License](https://img.shields.io/badge/License-Proprietary-red.svg)]

A pure-software, host-agnostic signal processing core developed 
by **Anyionic Technologies** to eliminate systemic skin pigmentation 
inaccuracies in dual-wavelength pulse oximetry systems.

---

## 🔴 The Problem

Standard commercial pulse oximeters measure blood oxygen 
saturation (SpO2) by analysing how oxygenated and deoxygenated 
haemoglobin absorb red (660nm) and infrared (940nm) light 
differently. However, melanin — the pigment determining skin 
tone — absorbs red light significantly more than infrared light, 
distorting the optical ratio and causing systematic SpO2 
overestimation in darker-skinned patients across Fitzpatrick 
Types IV-VI and the Monk Skin Tone scale.

This causes occult hypoxemia — a clinically dangerous condition 
where a monitor falsely reads safe blood oxygen levels (≥92%) 
while true arterial saturation is critically low — leading to 
delayed treatment decisions, documented in FDA safety 
communications since 2022.

---

## 🚀 The Solution: Software-Defined Compensation

Rather than requiring multi-wavelength hardware redesigns, 
Anyionic Technologies developed a pure mathematical compensation 
engine that optimises existing hardware. By evaluating real-time 
non-pulsatile optical attenuation, the algorithm dynamically 
classifies tissue properties and balances optical ratios 
without modifying any optoelectronic components.

### Architecture Overview

![Simulink Architecture Pipeline](Full_Model.png)

### Core Pipeline (6 Functional Blocks)

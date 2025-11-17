# Smart Rehab Companion

Empowering Home-Based Recovery with Intelligent Feedback

---

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [System Architecture](#system-architecture)
- [Hardware Requirements](#hardware-requirements)
- [Setup & Installation](#setup--installation)
- [Usage Guide](#usage-guide)
- [Firmware Overview](#firmware-overview)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

Smart Rehab Companion is an affordable, modular, and portable assistive hardware and software platform for post-surgical rehabilitation. This wearable, sensor-enabled solution offers **real-time feedback** on muscle activation, limb movement, and grip strength, thereby empowering patients with personalized exercise guidance and enabling **remote monitoring** for physiotherapists. Designed for scalability, energy efficiency, and user-friendliness, our companion system reduces the hassle of frequent clinic visits and supports faster, more consistent recovery.[1][2][4]

---

## Features

- **Multi-sensor integration:** Monitors muscle engagement (EMG), motion (IMU), and grip strength (Force sensor)[2][4]
- **Real-time feedback:** Visual guidance (LCD), LED, buzzer alerts
- **Remote supervision:** Wi-Fi/Bluetooth/App connectivity allowing therapists to monitor rehabilitation sessions remotely
- **Affordable and scalable:** Device cost targets below ₹7,000, designed for flexibility across multiple body parts[1]
- **User-centric:** Easy to use, robust, and energy-efficient for continuous in-home therapy
- **Future-ready:** Planned integration with AI-driven adaptive exercise correction, gamified interfaces, expanded sensor capabilities[2]

---

## System Architecture

### **Key Modules**
- **Wearable Band:** Forearm strap with AD8232 EMG, MPU6050 IMU, and FSR402 pressure sensors
- **Interactive Ball:** Grip device embedded with force and pressure sensors
- **Master Board:** Control and display center powered by Raspberry Pi Pico W, with LCD, buzzer, LED indicators
- **Mobile App/Cloud:** IoT interface for real-time data logging and remote physiotherapist access (Blynk app supported)

---

## Hardware Requirements

| Component           | Model                          | Function                                             |
|---------------------|-------------------------------|------------------------------------------------------|
| Microcontroller     | Raspberry Pi Pico W            | Data processing, sensor control, feedback, Wi-Fi/App  |
| EMG Sensor         | AD8232/MyoWare 2.0             | Muscle activation detection                          |
| IMU Sensor         | MPU6050                        | Wrist movement and angle tracking                    |
| Force Sensor       | FSR402/Interlink FSR406        | Grip strength inside interactive ball                 |
| Internal Pressure  | Honeywell MPRLS0025PA000/MS5837| Ball pressure regulation                             |
| LCD Module         | I2C 16x2 LCD                   | Visual feedback                                      |
| LED/Buzzer         | -                              | Corrective/alert feedback                            |
| Motor Driver       | DRV8833/L298N                  | Ball pressure adjustment                             |
| Battery            | TP4056 Li-Ion                  | Power supply, management                             |
| Sensor Interface   | Custom PCB                     | Integrated sensor and peripheral connection          |

---

## Setup & Installation

### Hardware
1. Assemble the wearable band (attach EMG and IMU sensors on forearm).[2]
2. Insert force sensor and pressure sensor into interactive grip ball.
3. Connect all sensor modules to master board via sensor interface PCB.[2]
4. Power using TP4056 Li-Ion battery, ensure BMS for protection.

### Software/Firmware
1. Install MicroPython or CircuitPython on Raspberry Pi Pico W.
2. Upload the provided `pico_w.py` firmware to the board.
3. Update WiFi credentials and Blynk token in the script as required.
4. Run program; LCD, buzzer, and LED indicate exercise status and feedback; data logs sent to Blynk app/cloud.

---

## Usage Guide

- **Wearing the Band:** Place EMG electrodes on Flexor Digitorum Superficialis & Pronator Teres. IMU sits on wrist. Launch master controller and app.[2]
- **Exercising:** Squeeze the interactive ball; feedback will be shown on LCD and via alerts. Correct/incorrect action triggers updates.
- **Remote Monitoring:** Therapist can access exercise progress and sensor data over Blynk app.[2][3]
- **Messages:**
    - "Doing Good!" = correct movement
    - "Muscle Not Activated - Try Again" = low EMG
    - "Take Rest!" = fatigue risk detected
    - LED/buzzer pulses for excessive/faulty grip or movement
---

## Firmware Overview (`pico_w.py`)[3]
- Reads analog signals from EMG, force sensors, and IMU.
- Sorts grip levels (no/light/medium/strong).
- Computes movement quality and triggers relevant feedback.
- Pushes data to Blynk app for real-time mobile updates.
- Designed for rapid prototyping, can be extended with calibration routines and advanced filtering.

---

## Contributing

Contributions are welcome! Open issues for bugs, improvements, or new features. For code updates, fork the repo and submit pull requests with clear documentation. Explore hardware extension ideas like improved sensor arrays or ML-based feedback.

---

## Contact

**Team: The Electronic Brigade**  
Chennai Institute of Technology, Chennai, India  
For queries or collaborations: shankarm.eee2023@citchennai.net

---

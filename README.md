# 🔥 Smart Fire & Gas Alarm System
Tinkercad Link For The Project 
https://www.tinkercad.com/things/bmI2aLeuBN2-fire-alarm-system-?sharecode=cLEaJ0aL8vUrT7CLTEg09KEBZ61UVab7AYNSLgDdmRA

## 🚀 Overview
This repository contains the source code and circuit design for an automated, multi-hazard safety system. Designed to detect combustible gases (smoke) and critical temperature spikes in real-time, this embedded system processes analog signals from environmental sensors and triggers tiered alerts to prevent fire-related disasters.

This project demonstrates practical applications of analog signal processing, voltage dividers, and embedded C++ programming, bridging the gap between hardware and software logic.

## ✨ Key Features
* **Dual-Sensor Monitoring:** Continuously tracks both ambient temperature (in °C) and combustible gas concentration.
* **Tiered Alert System:**
    * *Level 1 (Smoke Detection):* If gas/smoke exceeds the safe threshold, the Piezo Buzzer activates.
    * *Level 2 (High Heat):* If the temperature crosses the safety threshold, both the Buzzer and a visual red LED alert are triggered.
* **Real-Time Data Logging:** Raw and converted sensor values are continuously output to the Serial Monitor for system debugging and environmental tracking.
* **Auto-Reset:** Alarms automatically disengage once the environment returns to normal, safe levels.

## 🛠️ Hardware Requirements
To build this project physically or simulate it, you will need:
* 1x **Arduino Uno R3**
* 1x **LM35 Temperature Sensor** (Analog)
* 1x **MQ-2 Gas/Smoke Sensor** (Analog)
* 1x **Piezo Buzzer**
* 1x **Red LED**
* 1x **$4.7\text{k}\Omega$ Resistor** (Load resistor for the gas sensor)
* 1x **$220\Omega$ Resistor** (Current limiting for the LED)
* Breadboard and Jumper Wires

## 🔌 Circuit Connections
| Component | Arduino Pin | Notes |
| :--- | :--- | :--- |
| **MQ-2 Gas Sensor** | `A0` | Signal pin requires a pull-down resistor to GND. Top pins to 5V. |
| **LM35 Temp Sensor**| `A1` | Vout (middle pin) to A1. Left to 5V, Right to GND. |
| **Piezo Buzzer** | `D7` | Positive terminal to D7, Negative to GND. |
| **Red LED** | `D13`| Anode to D13 (via $220\Omega$ resistor), Cathode to GND. |

## 🧠 System Logic
The core logic relies on the Arduino's Analog-to-Digital Converter (ADC):
1.  **Temperature Processing:** The LM35 outputs a voltage proportional to the ambient temperature (10mV/°C). The Arduino reads this raw value on pin `A1`, applies a mathematical conversion `(raw * 500.0 / 1023.0) - 50.0`, and compares it against the defined threshold.
2.  **Gas Processing:** The MQ-2 sensor's internal resistance drops in the presence of smoke, creating a voltage spike on pin `A0`. 
3.  **Decision Making:** The C++ logic evaluates these states every 500 milliseconds. If either threshold is breached, digital output pins trigger the physical alarms.

## 💻 Simulation Note (Tinkercad)
This project was designed and tested in **Tinkercad**. To replicate real-world MQ-2 sensor physics in the simulation, a pull-down load resistor (e.g., $4.7\text{k}\Omega$) MUST be implemented on the analog output pin. This creates a necessary voltage divider, preventing a floating, constant 5V (1023) reading and allowing for accurate, variable smoke detection.

## 👨‍💻 About the Developer
**Anant Saxena**
*Electronics & Communication Engineering Student @ HNBGU*

I am an ECE undergraduate passionate about Embedded Systems Design, IoT, and bridging hardware with efficient software. Alongside my technical pursuits in Arduino and ARM architecture, I actively engage in leadership and communication roles as a Literary Captain and Anchor. 

---
*Always learning, always building.*

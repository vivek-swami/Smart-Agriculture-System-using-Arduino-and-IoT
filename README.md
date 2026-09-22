# Smart Agriculture System using Arduino and IoT

An Arduino/ATmega-based smart agriculture system that monitors soil moisture, temperature, humidity, and light, automates irrigation, and sends real-time SMS alerts over GSM — reducing manual monitoring and improving water-use efficiency on the farm.

## Overview

Traditional farming relies heavily on manual observation to decide when to irrigate or adjust growing conditions, which wastes water and labor. This project automates that decision-making: sensors continuously read field conditions, the microcontroller compares them against set thresholds, and actuators (pump, fan, grow light) are switched on or off automatically. A GSM module keeps the farmer informed remotely via SMS, and an LCD gives live on-site readings.

## Features

- **Real-time environmental monitoring** — soil moisture, temperature, humidity, and light intensity
- **Automated irrigation** — pump switches on/off based on soil-moisture threshold, no manual checking needed
- **Automated climate control** — fan and grow light actuated via relay based on sensor readings
- **Remote SMS alerts** — GSM/GPRS module (SIM900A) sends condition updates and can be configured via AT commands
- **On-site LCD display (16x2)** — live readout of sensor values and system status
- **Buzzer alerts** for threshold/fault conditions
- **Relay-driven 230V AC loads** (pump, bulb, fan) switched safely via a ULN2003A driver

## Hardware Used

| Component | Purpose |
|---|---|
| ATmega microcontroller (Arduino core) | System controller |
| Soil Moisture Sensor | Detects soil water content, drives irrigation logic |
| DHT11 Temperature & Humidity Sensor | Environmental monitoring |
| LDR / Light Sensor | Light-intensity monitoring |
| Submersible DC Water Pump | Irrigation actuator |
| GSM/GPRS Modem (SIM900A) | Remote SMS alerts and monitoring |
| 16x2 LCD Display | Local status/readout |
| ULN2003A Relay Driver + 3x Relay (12V) | Switches Pump, Bulb, and Fan on 230V AC |
| 7805 Voltage Regulator | 5V regulated supply for logic circuitry |
| Buzzer, LEDs, push switch | Status indication and manual control |

## Circuit Diagram

![Circuit Diagram](circuit_diagram.jpeg)

The microcontroller reads the soil moisture, humidity, and light sensors (via an LM393-based comparator front end), processes the readings, and drives the ULN2003A relay driver to switch the pump, bulb, and fan. The GSM module connects over serial (TXD/RXD) for SMS alerts, and the 7805 regulator supplies clean 5V from the AC-derived supply.

## How It Works

1. Sensors continuously report soil moisture, temperature, humidity, and light levels to the microcontroller.
2. The microcontroller compares each reading against a predefined threshold.
3. If soil moisture drops below the threshold, the pump is switched on automatically; it switches off once the threshold is met again.
4. Temperature/light readings similarly control the fan and grow light relays.
5. Current readings are shown on the LCD in real time.
6. The GSM module sends an SMS update on field conditions, so the system can be monitored remotely without being on-site.

## Software

- Written in Arduino C/C++ (Arduino IDE)
- Circuit designed and simulated in **Proteus** (ISIS for schematic/simulation, ARES for PCB layout)
- Key libraries: `DHT.h` (temperature/humidity), `LiquidCrystal.h` (LCD), `SoftwareSerial.h` (GSM communication)

## Advantages

- Optimizes resource usage through automated, sensor-driven control
- Reduces water wastage via precise, threshold-based irrigation
- Improves crop yield by maintaining more consistent growing conditions
- Enables remote monitoring, cutting down on the need for physical field visits

## Applications

- Crop farming and irrigation automation
- Greenhouse climate management
- Precision agriculture / site-specific resource management
- Educational and research platform for agri-tech experimentation

## Future Scope

- Add Wi-Fi/cloud connectivity for a web/app dashboard alongside GSM alerts
- Integrate soil NPK/pH sensing for nutrient management
- Add solar power support for off-grid deployment
- Data logging for historical trend analysis and yield correlation

## Project Info

Diploma capstone project — Electronics Engineering, Puranmal Lahoti Government Polytechnic, Latur (2023–2024).

**Team:** Mujawar Saad Alam, Shaikh Shahid Mahemud, Swami Vivekanand Shivshankar, Shaikh Mujaffar Majjid
**Guide:** Smt. R. H. Pawar, Department of Electronics Engineering

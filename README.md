# DIY ESP32 Drone Controller & Flight Controller Learning Journey

A 4-day hands-on learning project focused on understanding drone hardware, ESP32-based flight controllers, Betaflight configuration, ESCs, motors, and open-source drone firmware.

---

# Project Goal

The main goal of this project is to deeply understand:

* Drone hardware architecture
* Flight controller systems
* ESC and brushless motor working
* Power distribution in drones
* Betaflight configuration
* ESP32-based open-source flight controller development

This repository contains notes, documentation, hardware references, simulations, images, and learning progress collected during practical sessions.

---

# What I Learned

## Day 1

* Basic drone architecture
* Components of a quadcopter
* Introduction to flight controllers
* ESC basics
* Brushless motors
* Drone communication systems

![DRONE ARCHITECTURE](../BETAFLIGHT.jpeg)

## Day 2

* ESP32 transmitter design
* Joystick connections
* Channel mapping
* NRF24 communication basics
* Hardware pin configuration
* RC channel structure

![FLIGHT CONTROLLER](../CIRCUIT_DRONE.jpeg)

## Day 3

* Betaflight setup and configuration
* Receiver mapping
* Motor configuration
* Calibration concepts
* Sensor understanding
* Flight controller workflow

![Transmitter Diagram](../CIRCUIT_DRONE4.jpeg)

## Day 4

* F450 drone frame structure
* Power Distribution Board (PDB)
* ESC internal architecture
* MOSFETs and gate driving
* BEC (Battery Elimination Circuit)
* Back EMF in brushless motors
* XT60 connectors
* Li-ion vs LiPo batteries
* ESC calibration using servo tester
* Betaflight motor testing
* Safety precautions while testing drones

![BETAFLIGHT](../BETAFLIGHT.jpeg)

---

# Hardware Used

* ESP32 LOLIN32
* MPU6050
* F450 Drone Frame
* A2212 1000KV Brushless Motors
* SimonK 30A ESC
* XT60 Connector
* Joysticks
* Li-ion Battery Pack
* Betaflight Configurator

---

# Open Source Flight Controller Used

This project was inspired and supported by the open-source project:

## ESP-FC

An ESP32-based open-source flight controller firmware project.

### Repository

[ESP-FC GitHub Repository](https://github.com/rtlopez/esp-fc?utm_source=chatgpt.com)

### Features

* ESP32 flight controller firmware
* Betaflight compatible
* Supports MPU6050 / MPU9250
* Supports DSHOT protocols
* Supports SBUS / CRSF / IBUS receivers
* WiFi + ESP-NOW support
* Blackbox logging
* PID tuning
* RPM filtering
* Open-source and customizable

### Credits

Huge respect to the contributors and maintainers of the ESP-FC project for making open-source drone development accessible for students and hobbyists.

---

# Software Used

* Betaflight Configurator
* ESP Tool
* GitHub

---

# Repository Contents

* Documentation
* Hardware images
* Wiring references
* Betaflight screenshots
* ESP32 transmitter configuration
* Drone assembly references
* Learning notes

---

# Important Safety Notes

* Always remove propellers while testing motors
* Double-check polarity before connecting batteries
* Never short XT60 terminals
* Test ESCs carefully
* Verify motor direction before flight
* Use proper LiPo safety practices

---

# Future Plans

* Build custom ESP32 flight controller PCB
* Implement telemetry system
* Add GPS support
* Build long-range communication
* Learn PID tuning deeply
* Develop custom drone firmware features

---

# Status

Learning & Development Phase 🚀

---

# Author

Joslin Joseph

IoT | Embedded Systems | Drone Systems | PCB Design | ESP32 Development

---

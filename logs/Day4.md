# Day 4 – Drone Hardware & Betaflight 

## Overview

Day 4 was about learning how a drone works internally:

* Drone hardware parts
* ESCs and motors
* Battery and power system
* Flight controller
* Betaflight software

The goal was to understand how all parts connect together to make the drone fly.

---

# 1. Main Parts of a Quadcopter

A quadcopter contains:

1. Frame
2. PDB (Power Distribution Board)
3. ESCs
4. Brushless Motors
5. Propellers
6. Flight Controller
7. Receiver + Transmitter
8. Battery
9. Betaflight Firmware

---

# 2. Signal & Power Flow

## Control Signal Flow

```text
Transmitter → Receiver → Flight Controller → ESC → Motor
```

## Power Flow

```text
Battery → PDB → ESC → Motors
```

---

# 3. F450 Frame

The drone used an **F450 frame**.

### Features

* X-shaped frame
* 4 arms for motors
* Supports 10-inch propellers
* Stable beginner frame

### Material

* Arms → Plastic
* Center plate → FR4 (PCB-like material)

The center plate is not only a frame part.

It also works as a:

```text
Power Distribution Board (PDB)
```

---

# 4. Power Distribution Board (PDB)

## Purpose

The PDB distributes battery power to all ESCs.

Instead of:

```text
Battery → ESC1
Battery → ESC2
Battery → ESC3
Battery → ESC4
```

It becomes:

```text
Battery → PDB → All ESCs
```

### Inside the PDB

* Positive pads connected together
* Negative pads connected together
* Thick copper traces carry high current

---

# 5. ESC (Electronic Speed Controller)

## Purpose

ESC controls the speed of the brushless motor.

It:

* Receives signal from flight controller
* Converts DC battery power into 3-phase output
* Spins the motor

---

## ESC Connections

### Power Input

| Wire  | Purpose          |
| ----- | ---------------- |
| Red   | Battery Positive |
| Black | Ground           |

### Motor Output

3 thick wires go to the brushless motor.

### Signal Wires

| Wire   | Purpose        |
| ------ | -------------- |
| Signal | Control signal |
| GND    | Common ground  |
| VCC    | Optional power |

---

# 6. Inside an ESC

Main components inside ESC:

## MOSFETs

Used for high-speed switching.

```text
3 phases × 2 MOSFETs = 6 MOSFETs
```

---

## Microcontroller

Controls:

* Motor timing
* Speed
* Switching sequence

---

## Capacitor

Large capacitor helps to:

* Reduce voltage spikes
* Improve stability
* Protect MOSFETs

---

# 7. Brushless Motor

Motor used:

```text
A2212/13T 1000KV
```

## Meaning

| Part   | Meaning          |
| ------ | ---------------- |
| 2212   | Motor size       |
| 13T    | 13 winding turns |
| 1000KV | RPM per volt     |

---

# 8. KV Rating

## Meaning of KV

```text
RPM per Volt
```

Example:

```text
11.1V × 1000KV = 11100 RPM
```

---

## Low KV vs High KV

### Low KV

* More torque
* Bigger propellers
* Stable flight

### High KV

* More speed
* Smaller propellers
* Racing drones

---

# 9. Propellers

## Important Relation

```text
Large propeller → Low KV motor
Small propeller → High KV motor
```

This build uses:

| Component | Value   |
| --------- | ------- |
| Frame     | F450    |
| Motor     | 1000KV  |
| Propeller | 10 inch |

Good beginner setup.

---

# 10. Sensorless Motor Control

Brushless motors here have:

```text
No encoder
```

So ESC uses:

```text
Back EMF detection
```

to know motor position.

This method is called:

```text
Sensorless BLDC Control
```

---

# 11. BEC (Battery Elimination Circuit)

Battery voltage is too high for electronics.

Example:

```text
11.1V battery
```

But flight controller needs:

```text
5V
```

So BEC converts:

```text
11.1V → 5V
```

---

# 12. XT60 Connector

Main battery connector.

### Features

* High current support
* Reliable connection
* Low resistance

### Safety

Never short positive and negative terminals.

Possible risks:

* Sparks
* Battery damage
* Fire

---

# 13. Battery Learning

Observed battery:

```text
3S Li-ion battery
```

## 3S Meaning

```text
3 cells connected in series
```

### Voltage

| State   | Voltage |
| ------- | ------- |
| Nominal | 11.1V   |
| Full    | 12.6V   |
| Low     | ~9V     |

---

## Safety Notes

Problems observed:

* Direct soldering
* Weak insulation
* No visible BMS

Possible risks:

* Heating
* Fire
* Cell imbalance

For drones:

```text
LiPo batteries are preferred
```

because they can deliver high current.

---

# 14. Flight Controller

The flight controller is the:

```text
Brain of the drone
```

It:

* Reads receiver input
* Reads sensors
* Stabilizes drone
* Controls ESCs

---

# 15. Betaflight

## What is Betaflight?

Betaflight is:

* Flight controller firmware
* Drone configuration software

Used for:

* Sensor setup
* Motor testing
* Receiver setup
* Flight mode setup

---

# 16. Betaflight Setup Learning

The 3D model moved when the drone was tilted.

This confirmed:

* Gyroscope working
* Accelerometer working

---

## Accelerometer Calibration

Purpose:

```text
Set level position
```

Important:

* Keep drone on flat surface during calibration.

---

# 17. Motor Tab

Observed:

```text
QUAD X
```

Meaning:

* X-shaped quadcopter configuration

---

## Motor Testing

Betaflight allows motor testing using sliders.

### Important Safety

```text
Remove propellers before testing
```

to avoid injury.

---

# 18. ESC Calibration

Purpose:

```text
Match throttle range
```

between:

* Flight controller
* ESC

Basic steps:

1. Max throttle
2. Connect battery
3. ESC calibration mode
4. Lower throttle
5. Save range

---

# 19. Receiver Tab

## Channels

| Channel  | Function         |
| -------- | ---------------- |
| Roll     | Left/Right       |
| Pitch    | Forward/Backward |
| Yaw      | Rotation         |
| Throttle | Motor power      |
| AUX      | Extra switches   |

---

## Channel Mapping

Observed:

```text
AETR1234
```

Meaning:

| Letter | Function |
| ------ | -------- |
| A      | Roll     |
| E      | Pitch    |
| T      | Throttle |
| R      | Yaw      |

---

# 20. Important Safety Points

## Always Remove Propellers During Testing

Motors may suddenly spin and cause injury.

---

## Check for Shorts

Before connecting battery:

* Check solder joints
* Check positive/negative pads
* Check loose wires

---

## Battery Safety

Never:

* Short battery
* Overcharge
* Puncture LiPo
* Leave charging unattended

---

# 21. Main Concepts Learned

## Electronics

* MOSFET switching
* PWM control
* Voltage regulation
* Power distribution
* Back EMF detection

---

## Drone Concepts

* ESC calibration
* Motor direction
* Flight stabilization
* Receiver mapping

---

## Software

* Betaflight setup
* Motor testing
* Sensor calibration

---

# 22. Full Drone Architecture

## Power System

```text
Battery
   ↓
XT60
   ↓
PDB
   ↓
ESC
   ↓
Motor
   ↓
Propeller
```

## Control System

```text
Transmitter
   ↓
Receiver
   ↓
Flight Controller
   ↓
ESC Signal
   ↓
Motor Speed
```

---

# 23. Key Learning from Day 4

Previously:

* Drone looked like separate components

Now understood:

* Full power flow
* Full control flow
* ESC working principle
* Motor and propeller relationship
* Betaflight basics

---

# 24. Future Topics to Learn

## Electronics

* MOSFET gate driving
* PCB design
* Current sensing

## Drone Systems

* PID tuning
* GPS
* FPV systems
* Telemetry

## Embedded Systems

* STM32
* ESP32 communication
* Sensor fusion

---

# 25. Final Summary

Day 4 helped in understanding:

* Drone hardware architecture
* ESC and motor working
* Battery and PDB system
* Betaflight setup
* Flight controller operation

This connected:

```text
Electronics + Embedded Systems + Flight Control
```

into one complete drone system understanding.

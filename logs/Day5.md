# Day 5 – Debugging, Hardware Failure Analysis & Final Flight Test

## Objective
The primary objective of Day 5 was to complete the drone assembly, install the propellers, perform motor testing, and achieve the first successful flight.

---

## Initial Status
By the end of Day 4:
* Drone frame assembly was completed.
* Motors and ESCs were mounted.
* Flight controller firmware was configured.
* Radio transmitter and receiver communication was working.
* Betaflight configuration was completed.

The only remaining task was:
* Install propellers
* Verify motor operation
* Perform the first flight test

---

## Problem 1: One Motor Not Spinning
During the initial motor test, we observed that:
* Three motors were operating normally.
* One motor was not spinning.

### Investigation
To identify the issue:
1. Motor connections were checked.
2. ESC connections were verified.
3. Betaflight motor outputs were tested.
4. A servo tester was used to independently test the ESC and motor.

### Observation
When tested using the servo tester:
* The ESC worked correctly.
* The motor spun normally.

This confirmed that:
* The motor was healthy.
* The ESC was healthy.
* The problem was located in the flight controller output system.

---

## GPIO Pin Debugging
The team then tested each motor output channel individually.

### Procedure
* Different ESP32 GPIO outputs were assigned to the ESC.
* Each channel was tested one by one.

### Result
The investigation revealed that:
**GPIO25 was not functioning properly.**

Because the ESC signal was connected to this pin:
* The corresponding motor never received a valid control signal.

### Solution
The motor output was reassigned:
* From **GPIO25**
* To **GPIO26**

After updating the firmware configuration:
* The motor began spinning successfully.

---

## Problem 2: ESP32 Failure
Shortly after fixing the GPIO issue:
* The system suddenly stopped functioning.
* USB communication was lost.

### Observation
The ESP32 could no longer:
* Connect to the computer
* Upload firmware
* Communicate with Betaflight

### Conclusion
The ESP32 development board had failed. 

The exact cause could not be confirmed, but possible reasons include:
* Faulty GPIO circuitry
* Electrical stress
* Short circuit during testing
* Internal board failure

---

## Replacement Attempt
Since no new ESP32 board was available:
* The mentors provided an older ESP32 board.

### Actions
1. Firmware was uploaded.
2. Configuration was restored.
3. System testing resumed.

### New Issue
The replacement ESP32:
* Heated excessively.
* Became unstable.

After approximately 13 minutes:
* The second ESP32 also failed.

At this point:
* Two ESP32 boards had become unusable.
* The flight controller was no longer operational.

---

## Temporary Setback
The team was disappointed because:
* Four days of work had gone into building the drone.
* The final flight could not be performed with our own flight controller.

However, the team continued participating in testing and observing other groups.

---

## Team 2 Flight Demonstration
Another team successfully completed their drone. 

Their drone:
* Passed testing.
* Achieved stable flight.
* Demonstrated correct operation of the complete system.

This allowed us to observe:
* Flight controller stabilization
* Motor synchronization
* ESC response
* Quadcopter control behavior

---

## Final Solution
Since our drone hardware was correctly assembled:
* Motors were functioning.
* ESCs were functioning.
* Frame assembly was complete.

We requested permission to use the working flight controller from Team 2. The controller was installed on our drone.

---

## Successful Flight
After installing the replacement flight controller:
* The drone armed successfully.
* Motors operated correctly.
* Lift-off was achieved.

### Flight Results
* Stable takeoff
* Good balance
* Reliable control response
* Higher altitude than expected
* Smooth flight performance

The drone flew successfully and demonstrated that:
* Our mechanical assembly was correct.
* Our wiring was correct.
* The major obstacle was the failed GPIO/ESP32 hardware.

---

## Key Technical Concepts Learned

### 1. Systematic Debugging
Never assume a component is faulty. Instead:
* Test each subsystem individually.
* Eliminate possibilities one by one.

### 2. ESC Testing with Servo Tester
A servo tester can directly generate PWM signals to:
* Verify ESC operation
* Verify motor operation
* Isolate flight controller issues

### 3. GPIO Failure Diagnosis
Microcontroller pins can fail independently. Symptoms include:
* Missing output signals
* Unresponsive peripherals
* Partial system operation

### 4. Hardware Redundancy
Having spare hardware is important because:
* Development boards may fail.
* Field replacements save project time.

### 5. Teamwork in Engineering
Engineering projects often require:
* Collaboration
* Sharing resources
* Collective troubleshooting

The final successful flight was achieved through teamwork and mutual support.

---

## Final Reflection
Day 5 demonstrated that engineering is not only about building systems but also about solving unexpected problems. 

Although two ESP32 boards failed and significant debugging was required, the project concluded with a successful drone flight. The experience provided practical knowledge in flight controller configuration, ESC calibration, motor testing, hardware troubleshooting, and real-world collaboration. 

The successful flight served as a rewarding conclusion to five days of learning and hands-on development.

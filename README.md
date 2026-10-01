# CAN-Driven-Vehicle-Monitoring-and-Driver-Assistance-System
## Project Overview

The **CAN-Driven Vehicle Monitoring and Driver Assistance System** is a three-node embedded system designed to monitor important vehicle parameters and provide driver assistance features using **CAN (Controller Area Network) communication**.

The system monitors **fuel level and engine temperature**, controls vehicle indicators, detects obstacles during reverse operation, and displays real-time vehicle information on a centralized LCD dashboard.

The project is implemented using **LPC2129 microcontrollers** and CAN transceivers. The system is divided into three nodes: **Main Node, Indicator & Reverse Alert Node, and Fuel Node**. Each node performs a specific function and communicates with other nodes through the CAN bus.

The project demonstrates the practical use of **Embedded C, ADC, external interrupts, CAN communication, LCD interfacing, ultrasonic sensing, and sensor-based monitoring**.

---

## Features

- Real-time engine temperature monitoring
- Fuel percentage monitoring
- CAN-based communication between multiple nodes
- Forward and Reverse mode selection
- Left and Right indicator control
- Reverse obstacle detection
- SAFE, WARNING, and STOP alerts
- Buzzer-based reverse warning
- LCD-based vehicle status display
- External interrupt-based switch handling
- ADC-based fuel level measurement

---

## System Architecture

The system consists of three main nodes connected through the CAN communication bus:

```text
                    CAN BUS
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
+---------------+ +---------------+ +---------------+
|   Main Node   | | Indicator &   | |   Fuel Node  |
|               | | Reverse Alert | |               |
| LPC2129       | | Node          | | LPC2129       |
|               | |               | |               |
| LCD           | | LPC2129       | | Fuel Gauge    |
| Temperature   | | HC-SR05       | | ADC           |
| Mode Switch   | | LEDs          | |               |
| Indicators    | | Buzzer        | |               |
+---------------+ +---------------+ +---------------+
```

## CAN Communication Flow

```text
                         CAN BUS
                            |
        +-------------------+-------------------+
        |                   |                   |
        v                   v                   v
   MAIN NODE          INDICATOR &            FUEL NODE
                      REVERSE ALERT
        |                   |                   |
   +----+----+          +---+---+          +----+----+
   |    |    |          |   |   |          |         |
   v    v    v          v   v   v          v         v
 LCD  Temp  Switches   LED Buzzer HC-SR05  Fuel     ADC
                                            Gauge

The three nodes communicate through the CAN bus while each node interfaces with its dedicated peripherals. This distributed architecture allows vehicle monitoring, indicator control, fuel monitoring, and reverse obstacle detection to operate together as a single system.
```
## Hardware Components

| Hardware Component | Purpose |
|---|---|
| **LPC2129 Microcontroller** | Controls the system |
| **CAN Transceiver (MCP2551)** | Enables CAN communication |
| **LCD** | Displays vehicle information |
| **HC-SR05 Ultrasonic Sensor** | Detects obstacles |
| **Fuel Gauge** | Measures fuel level |
| **LEDs** | Shows vehicle status |
| **Buzzer** | Gives warning alerts |
| **Switches** | Selects modes and controls indicators |
| **USB to UART Converter** | Provides serial communication |

## Project Structure

```text
CAN-Driven-Vehicle-Monitoring-and-Driver-Assistance-System/
│
├── Main_Node/
│   ├── main.c
│   ├── can.c
│   ├── lcd.c
│   ├── adc.c
│   ├── temperature.c
│   └── interrupt.c
│
├── Indicator_Reverse_Alert_Node/
│   ├── main.c
│   ├── can.c
│   ├── ultrasonic.c
│   ├── led.c
│   └── buzzer.c
│
├── Fuel_Node/
│   ├── main.c
│   ├── can.c
│   ├── adc.c
│   └── fuel.c
│
├── README.md
└── LICENSE
```
## System Working

The system consists of three CAN-connected nodes that work together for vehicle monitoring and driver assistance.

1. **Main Node**  
   Continuously reads engine temperature and receives fuel percentage through CAN. It monitors the vehicle mode and sends indicator commands in Forward Mode. In Reverse Mode, it receives the reverse alert status and displays **SAFE, WARNING, or STOP** on the LCD.

2. **Indicator & Reverse Alert Node**  
   Controls the left and right indicators in Forward Mode. In Reverse Mode, it enables the HC-SR05 ultrasonic sensor to detect obstacles. Based on the obstacle distance, it generates **SAFE, WARNING, or STOP** alerts using the buzzer and LED, and sends the status to the Main Node through CAN.

3. **Fuel Node**  
   Reads the fuel gauge using the LPC2129 ADC, converts the ADC value into fuel percentage, and periodically sends the fuel percentage to the Main Node through CAN. It also sends an updated value when there is a significant change in fuel level.

4. **Overall Operation**  
   The three nodes continuously exchange information through the **CAN bus**. The Main Node displays the engine temperature, fuel percentage, vehicle mode, and reverse alert status on the LCD.

## Project Workflow

```text
                    START
                      |
                      v
        Create Project and Node Folders
                      |
                      v
          Test Individual Modules
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
         LCD         ADC       Interrupts
          |           |           |
          +-----------+-----------+
                      |
                      v
            Test Ultrasonic Sensor
                      |
                      v
          Test Temperature Sensor
                      |
                      v
             Test CAN Communication
                      |
                      v
          Develop Software for Nodes
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
      Main Node   Indicator &     Fuel Node
                  Reverse Alert
                      |
                      v
              Integrate All Nodes
                      |
                      v
              Test Complete System
                      |
                      v
                     END
```
## Dashboard 
 
The Main Node LCD displays: 
 
```text
╔══════════════════════════════════╗ 
║       VEHICLE MONITORING         ║ 
╠══════════════════════════════════╣ 
║  Engine Temp : XX °C             ║ 
║  Fuel Level  : XX %              ║ 
║  Mode        : FORWARD/REVERSE   ║ 
║  Alert       : SAFE/WARNING/STOP ║ 
╚══════════════════════════════════╝
```

## Applications

- Automotive vehicle monitoring systems
- Driver assistance and safety systems
- Real-time vehicle status monitoring
- Fuel and engine condition monitoring
- Reverse parking and obstacle detection
- Vehicle indicator control systems
- CAN-based automotive communication
- Embedded automotive control systems
- Centralized vehicle information dashboards
- Educational and prototype automotive projects

## Development Tools and Environment

- **Programming Language:** Embedded C
- **Microcontroller:** LPC2129
- **IDE / Compiler:** Keil µVision
- **Programming Tool:** Flash Magic
- **Communication Protocol:** CAN
- **CAN Transceiver:** MCP2551
- **Development Environment:** Embedded System Hardware and Software

## Future Scope

- Add GPS for real-time vehicle location tracking.
- Add IoT connectivity for remote vehicle monitoring.
- Add mobile application support for viewing vehicle status.
- Add more sensors for advanced vehicle monitoring.
- Improve obstacle detection using advanced sensors.
- Add data logging for storing vehicle information.
- Enhance the system with automatic safety and alert features.
- Expand CAN communication for more vehicle monitoring and control functions.

## Developed By
B.Vedha Sri







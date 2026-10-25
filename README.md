# Smart Biometric Attendance System

An Arduino-based biometric attendance system that combines fingerprint authentication, keypad-based administration, Python automation, WhatsApp notifications, and digital attendance logging.

## Overview

The Smart Biometric Attendance System is designed to automate attendance recording using an Arduino Uno and an R307 fingerprint sensor. The system authenticates users through their fingerprints and communicates attendance events to a Python script running on a connected computer.

The Python component processes incoming serial messages, supports automated WhatsApp notifications, and maintains a digital attendance log in CSV format.

This project demonstrates the integration of embedded systems, hardware interfacing, serial communication, and Python automation.

## Key Features

- **Fingerprint Authentication:** Identifies registered users using an R307 fingerprint sensor.
- **Attendance Logging:** Records attendance events with timestamps in a CSV file.
- **WhatsApp Notifications:** Supports automated notifications through a Python automation script.
- **LCD Feedback:** Displays system prompts and status information on a 16×2 I2C LCD.
- **Keypad Administration:** Provides a keypad interface for administrative operations.
- **User Enrollment:** Supports registering fingerprints through a guided enrollment process.
- **Fingerprint Management:** Supports deleting registered fingerprint IDs.

## Hardware Components

| Component | Purpose |
|---|---|
| Arduino Uno | Main microcontroller |
| R307 Fingerprint Sensor | Fingerprint authentication |
| 16×2 I2C LCD | User feedback and system status |
| 4×4 Keypad | Administrative input |
| Green LED | Access-granted indicator |
| Red LED | Access-denied indicator |
| Buzzer | Audible feedback |
| Computer | Runs the Python automation script |

## Software & Technologies

- C++ / Arduino
- Python
- Serial Communication
- CSV File Handling
- Fingerprint Sensor Integration
- WhatsApp Web Automation

## System Architecture

The system consists of two main components:

**1. Arduino Firmware**

The Arduino interfaces with the fingerprint sensor, LCD, keypad, and indicators. It handles fingerprint enrollment, authentication, and administrative operations.

**2. Python Automation**

A Python script runs on a connected computer and reads messages from the Arduino through the serial port. Attendance events can trigger automated WhatsApp notifications and be recorded in a CSV file.

### Communication Protocol

The Arduino sends an attendance event through the serial connection using the following message format:

```text
LOGIN:ID
```

Example:

```text
LOGIN:7
```

Here, `7` represents the registered fingerprint ID associated with the attendance event.

The Python script reads the incoming message and processes the extracted user ID.

## Repository Structure

```text
Smart-Biometric-Attendance-System/
├── Arduino-Code.cpp
├── python.py
├── attendance_log.csv
├── Conceptual Design/
├── Physical Prototype/
└── README.md
```

## Getting Started

### Prerequisites

- Arduino Uno
- R307 fingerprint sensor
- Compatible LCD and keypad modules
- Arduino IDE
- Python 3
- USB connection between the Arduino and computer
- WhatsApp Web access if notification automation is enabled

### 1. Configure the Arduino

1. Open `Arduino-Code.cpp` and review the firmware.
2. Install the required Arduino libraries based on the actual `#include` statements in the source code.
3. Connect the hardware according to the wiring configuration used in the project.
4. Select the correct Arduino board and serial port in the Arduino IDE.
5. Compile and upload the firmware.

**Note:** Confirm whether `Arduino-Code.cpp` can be opened directly as an Arduino sketch or should be placed in a matching `.ino` sketch folder.

### 2. Configure Python

1. Ensure Python 3 is installed.
2. Open `python.py` and review its imports and configuration settings.
3. Install the dependencies required by the script. For example, if the source code imports these packages:

```bash
pip install pyserial pywhatkit pyautogui
```

4. Configure the correct serial port and any required notification settings.
5. Connect the Arduino and close any other application using the same serial port.
6. Run the script:

```bash
python python.py
```

The dependency list above is a starting point based on the project's documented automation approach. Verify the actual imports before installing packages.

### 3. Verify the System

- Confirm that the Arduino initializes successfully.
- Test fingerprint enrollment and authentication.
- Verify that the expected serial message is received by Python.
- Confirm that attendance records are written correctly.
- Test WhatsApp notification automation separately, if enabled.

## Administrative Operations

The documented keypad workflow includes the following operations:

| Key / Input | Operation |
|---|---|
| `#` | Enter the administrative authentication screen |
| `1234` followed by `*` | Authenticate using the documented default PIN |
| `1` | Start fingerprint enrollment |
| `2` | Start fingerprint deletion |
| `0` | Exit administrative mode |

These controls reflect the documented project design. Confirm the exact sequence against the current Arduino firmware before operating the system.

## Project Design

The repository includes the following supporting materials:

- **Conceptual Design:** Project design documentation and planning materials.
- **Physical Prototype:** Materials documenting the hardware implementation.

Add genuine project photographs and design diagrams to these folders and link them here once the image filenames are confirmed.

## Future Improvements

- Integrate a database such as SQLite or MySQL.
- Generate daily and monthly attendance reports.
- Build an administrative dashboard for attendance management.
- Add optional door-lock control using a relay.
- Improve configuration management and authentication security.
- Add automated tests and more robust serial error handling.

## Security Considerations

- Change default administrative credentials before real-world use.
- Keep phone numbers, credentials, and other private configuration out of public source code.
- Protect attendance records because they may contain personal information.
- Test hardware and automation in a controlled environment before deployment.

## License

This project is intended to be distributed under the MIT License. Include a `LICENSE` file in the repository if one is not already present.



- GitHub: [@Romana-18](https://github.com/Romana-18)

---

*Built to explore the practical integration of embedded systems, biometric authentication, and software automation.*

# Knee Rehabilitation Orthosis – Extension Assistance During Walking (IoT Platform)

Final-year project (EC19811) – B.E. Electronics and Communication Engineering,
Rajalakshmi Engineering College (Autonomous), Chennai – April 2025.

**Authors:** Vengatesh R, Vinoth Kumar P
**Supervisor:** Dr. M. Palanivelan, M.E., Ph.D., Professor, Dept. of ECE

> Accepted at the 13th International Conference on Contemporary Engineering and Technology (ICCET 2025).

## Overview

Knee joint pain from bone-on-bone compression is common in elderly people and in those with
musculoskeletal conditions such as knee osteoarthritis (OA). This project is a prototype
wearable system that senses foot pressure and knee motion during walking, with the goal of
assisting knee extension and offloading the joint by transferring weight to the foot through
a supportive shoe interface. Sensor data can be sent over Bluetooth to a mobile device for
remote monitoring and IoT-based analysis.

The prototype demonstrated knee extension and could lift a load of up to 17 kg.

## Hardware

| Component | Purpose |
|-----------|---------|
| Arduino Uno (ATmega328) | Main controller |
| ADXL345 accelerometer (I2C) | Motion / joint angle data on X, Y, Z axes |
| Piezoelectric sensor | Foot impact / force sensing |
| Force / pressure sensor (FSR) | Foot pressure and weight distribution |
| HC-05 Bluetooth module | Wireless data transmission to mobile |
| Power supply unit, breadboard | Power and prototyping |

## Pin connections

| Sensor | Arduino Uno pin |
|--------|-----------------|
| ADXL345 SDA | A4 (SDA) |
| ADXL345 SCL | A5 (SCL) |
| ADXL345 VCC / GND | 3.3V or 5V / GND (depends on breakout board) |
| Piezoelectric sensor | A1 |
| Force / pressure sensor (FSR) | A0 |
| HC-05 TXD / RXD | D0 / D1 (or use SoftwareSerial on other pins) |

## Software requirements

- [Arduino IDE](https://www.arduino.cc/en/software)
- Libraries (install via Library Manager):
  - `Adafruit ADXL345`
  - `Adafruit Unified Sensor`
- Proteus (optional, for circuit simulation)

## Getting started

1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/knee-rehab-orthosis-iot.git
   ```
2. Open `firmware/knee_rehab_orthosis/knee_rehab_orthosis.ino` in the Arduino IDE.
3. Install the libraries listed above.
4. Select **Board: Arduino Uno** and your COM port, then upload.
5. Open the Serial Monitor at **9600 baud** to see live readings.

## Sample output

```
X: -2.86 m/s^2 | Y: -5.45 m/s^2 | Z: -7.65 m/s^2
Piezo raw reading: 512
FSR raw reading: 300
------------------------
```

Sample angle/acceleration measurements recorded in the report:

| Time | X axis | Y axis | Z axis |
|------|--------|--------|--------|
| 5 s  | -2.36  | -5.63  | -7.69  |
| 10 s | -1.36  | -4.96  | -8.36  |
| 15 s | -1.99  | -5.61  | -7.63  |

## System architecture

```
Piezo sensor ─┐
ADXL345 ──────┼─> Arduino Uno ─> Bluetooth (HC-05) ─> Mobile display / IoT cloud
Force sensor ─┘
```

Layers: wearable sensor layer → microcontroller → wireless transmission → cloud/server
storage → analytics (ML, planned) → web/mobile front end.

## Future work

- Vibratory feedback band for proprioceptive stimulation
- ML models (LSTM / CNN) for gait anomaly detection and recovery prediction
- Cloud storage, clinician dashboards and a patient mobile app
- Gamified exercises and a voice-guided assistant
- Adaptive torque control for the exoskeleton actuator

## Repository structure

```
knee-rehab-orthosis-iot/
├── firmware/
│   └── knee_rehab_orthosis/
│       └── knee_rehab_orthosis.ino
├── docs/
│   └── (add project report PDF, photos and circuit diagrams here)
├── .gitignore
├── LICENSE
└── README.md
```

## License

Released under the MIT License – see [LICENSE](LICENSE).

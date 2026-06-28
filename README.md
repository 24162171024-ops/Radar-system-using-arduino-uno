# Radar System using Arduino UNO

A homemade radar system that scans for objects using an ultrasonic sensor mounted on a servo motor, with a real-time visualization built in Processing.

## Project Structure

```
radar-system/
├── radar_arduino/
│   └── radar_arduino.ino     # Arduino sketch (C++) - controls servo, sensor, LEDs, buzzer
├── radar_visualizer.pde      # Processing sketch (Java) - draws the radar UI
└── README.md
```

## How it works

- `radar_arduino.ino` sweeps the ultrasonic sensor (HC-SR04) across 15°–165° using a servo, measures distance at each angle, and sends `angle,distance.` over Serial. It also drives a status LED, a green "scanning" LED, a red "detection" LED, and a buzzer based on how close a detected object is.
- `radar_visualizer.pde` reads that serial data in Processing and renders a classic sweeping radar display, drawing green sweep lines normally and red warning lines when an object is within 40cm.

## Setup

1. Wire the circuit per the project's circuit diagram (Arduino UNO, HC-SR04, SG90 micro servo, 2x LEDs, buzzer, slide switch, breadboard).
2. Open `radar_arduino/radar_arduino.ino` in the Arduino IDE, set the correct board/port, and upload.
3. Open `radar_visualizer.pde` in Processing.
   - Update the `size(...)` call in `setup()` to match your monitor's resolution.
   - Update the COM port string in `new Serial(this, "COM6", 9600)` to match your Arduino's port.
4. Run the Processing sketch — the radar sweep should sync with the physical servo.

## Components

- Arduino UNO
- HC-SR04 Ultrasonic Sensor
- 9g Micro Servo
- 2x LEDs (Red, Green) + 1x Red LED for status
- Buzzer
- Slide Switch
- 220Ω and 1kΩ resistors
- Jumper wires, USB A/B cable, breadboard


# Sensor-Testing-1-
Bug Report: Line Sensor Output Remains Constant
Problem

The Line Sensor digital output remains HIGH (1) regardless of the sensor state. In both Auto and Manual modes, toggling "Line Detected" between ON and OFF does not change the GPIO input value read by the Raspberry Pi Pico.

Connections
VCC → 3.3V
GND → GND
OUT → GP15
Test Code
from machine import Pin
import time

line = Pin(15, Pin.IN)

while True:
    if line.value():
        print("HIGH")
    else:
        print("LOW")
    time.sleep(0.5)

    Actual Output

The Serial Monitor continuously prints:

HIGH
HIGH
HIGH
...

The GPIO input value remains 1 regardless of the sensor state.

Expected Output

The GPIO input value should change according to the sensor state. For example:

Line Detected = ON
HIGH
HIGH
HIGH
...
Line Detected = OFF
LOW
LOW
LOW
...

The important behavior is that the GPIO value changes between 0 and 1 when the sensor state changes.

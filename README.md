
Servo Mirror Movement Project (Arduino UNO)

# Overview
This project demonstrates a mirrored movement using two servo motors connected to an Arduino UNO.  
Servo 1 moves from 0° to 90°, while Servo 2 moves in the opposite direction from 180° to 90°, then both reverse. The loop repeats continuously.

---

Components
- Arduino UNO
- 2 × Servo Motors (e.g., SG90)
- Jumper Wires
- USB Cable

---

 Circuit Connections

| Component | Signal Pin | Power (VCC) | Ground (GND) |
|-----------|------------|-------------|--------------|
| Servo 1   | D9         | 5V          | GND          |
| Servo 2   | D10        | 5V          | GND          |

---

💻 Arduino Code

```cpp
#include <Servo.h>

int pos = 0;

Servo servo_9;
Servo servo_10;

void setup() {
  servo_9.attach(9, 500, 2500);
  servo_10.attach(10, 500, 2500);
}

void loop() {
  for (pos = 0; pos <= 90; pos += 1) {
    servo_9.write(pos);
    servo_10.write(180 - pos);
    delay(15);
  }

  for (pos = 90; pos >= 0; pos -= 1) {
    servo_9.write(pos);
    servo_10.write(180 - pos);
    delay(15);
  }
}

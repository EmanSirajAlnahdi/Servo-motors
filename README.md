# Servo Arduino ProjectServo-motors
Arduino code and walking algorithm for controlling 4 servo motors in a robot.

---

## Components Used

- Arduino Uno
- 4 × Servo Motors
- Jumper wires
- Breadboard (optional)
- Tinkercad Circuit Simulator

---
## Servo Pin Mapping:
Servo	Function	Arduino Pin
Servo 1	Left Hip	3
Servo 2	Left Knee	5
Servo 3	Right Hip	6
Servo 4	Right Knee	9
## Power:
Servos powered from breadboard rails connected to Arduino 5V and GND.
<img width="1280" height="827" alt="image" src="https://github.com/user-attachments/assets/50c259fb-38ab-40df-a16b-9b9d9808b180" />

---

## Arduino Code
#include <Servo.h>

Servo servo1, servo2, servo3, servo4;

void setup() {
  servo1.attach(3);
  servo2.attach(5);
  servo3.attach(6);
  servo4.attach(9);
}

void loop() {
  // Sweep motion for 2 seconds
  unsigned long startTime = millis();
  while (millis() - startTime < 2000) {
    for (int pos = 0; pos <= 180; pos += 5) {
      servo1.write(pos);
      servo2.write(pos);
      servo3.write(pos);
      servo4.write(pos);
      delay(15);
    }
    for (int pos = 180; pos >= 0; pos -= 5) {
      servo1.write(pos);
      servo2.write(pos);
      servo3.write(pos);
      servo4.write(pos);
      delay(15);
    }
  }

  // Hold at 90 degrees
  servo1.write(90);
  servo2.write(90);
  servo3.write(90);
  servo4.write(90);
  while (true); // Stop the loop here
}

---

## Walking Motion Algorithm

This algorithm describes how to simulate a simple walking cycle for a biped robot using 4 servo motors :

- **Servo 1** → Left Hip  
- **Servo 2** → Left Knee  
- **Servo 3** → Right Hip  
- **Servo 4** → Right Knee

---

###  Walking Steps:

1. **Standing Position**  
   - All 4 servos set to 90° (robot is balanced and upright).

2. **Shift Weight to Left Leg**  
   - Keep Servo 1 and 2 (Left Hip and Knee) at 90°.

3. **Move Right Leg Forward**  
   - Servo 3 (Right Hip) → 135°  
   - Servo 4 (Right Knee) → 120°

4. **Place Right Leg Down**  
   - Gradually return Servo 3 and 4 back to 90°.

5. **Stabilize**  
   - Hold all servos at 90° for a short delay to simulate balance.

6. **Shift Weight to Right Leg**

7. **Move Left Leg Forward**  
   - Servo 1 → 135°  
   - Servo 2 → 120°

8. **Place Left Leg Down**  
   - Return Servo 1 and 2 to 90° gradually.

9. **Stabilize Again**  
   - Hold at 90° for a moment before repeating.

10. **Repeat steps 2–9**  
   - Continue this loop to simulate walking motion.

---

##  Project Simulation (Tinkercad)

You can try the project online here:  
[Open Circuit in Tinkercad](https://www.tinkercad.com/things/9MHjAkKUmXJ/editel?returnTo=%2Fdashboard)

---

 ## Author: Eman Alnahdi.


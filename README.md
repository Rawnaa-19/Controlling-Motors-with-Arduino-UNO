# Controlling-Motors-with-Arduino-UNO
## Table of Contents : 
1. [Introduction](#Introduction)
1. [Servo Motor](#Servo-Motor)
   - [Sweep](#Sweep)
     - [Circuit Components](#Circuit-Components)
     - [Circuit Wiring](#Circuit-Wiring)
     - [Arduino Code](#Arduino-Code)
     - [Code simulation](Code-simulation)
   - [Knob]
     - [Circuit Components]
     - [Circuit Wiring]
     - [Arduino Code]
     - [Code simulation]
1. [DC Motor]
1. [References]

## Introduction
The second task for the Electronics and Power Department is controlling motors using Arduino UNO. There are two types of motors in this task: servo motors, which rotate 180 degrees, and DC motors, which can move in a clockwise or counterclockwise direction. 
## Servo Motor
The servo motor is an electrical device that rotates machines and robots in an angular direction.(The Purpose of Servo Motors | Fuji Electric Product Column | Fuji Electric Global, n.d.)
### Sweep 
Here the servo motor is controlled using Arduino UNO.
#### Circuit Components
1. Arduino UNO
2. Servo motor
3. Wires
4. Breadboard
#### Circuit Wiring
The servo motor has 3 wires (Vcc , Ground ,and Signal).The Vcc "Red" wire is connected to the 5V pin in the Arduino through the breadboard, the Ground "black" wire is connected to the GND "Ground" pin in the Arduino through the breadboard, and the signal "yellow" wire is connected to the 2 pin in the Arduino through the breadboard.

<kbd> **Figure 1** <br><br>Servo Motor Sweep Circuit <br><br> <kbd>![image](https://github.com/Rawnaa-19/Controlling-Motors-with-Arduino-UNO/assets/106926557/2b280aa9-9d0c-43d3-b071-99b350fa8fc6)</kbd></kbd>
#### Arduino Code
From the Arduino IDE **File>examples>servo>sweep** section, a ready to use code is provided.

<kbd>**Figure 2**<br><br>Arduino IDE sweep example<br><br> 
<kbd>![image](https://github.com/Rawnaa-19/Controlling-Motors-with-Arduino-UNO/assets/106926557/176ab61a-247b-485e-bbea-ca34b7da1239)</kbd></kbd>
<br><br>
The code uses servo library to control the servo motor. It rotates the servo shaft from 0 degrees to 180 and from 180 degrees to 0.
```
#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  for (pos = 0; pos <= 180; pos += 1) { // goes from 0 degrees to 180 degrees
    // in steps of 1 degree
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15 ms for the servo to reach the position
  }
  for (pos = 180; pos >= 0; pos -= 1) { // goes from 180 degrees to 0 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15 ms for the servo to reach the position
  }
}
```
#### Code simulation
[https://clipchamp.com/watch/ZPxos7zDe5f
](https://clipchamp.com/watch/ZPxos7zDe5f?utm_source=share&utm_medium=social&utm_campaign=watch)https://clipchamp.com/watch/ZPxos7zDe5f?utm_source=share&utm_medium=social&utm_campaign=watch

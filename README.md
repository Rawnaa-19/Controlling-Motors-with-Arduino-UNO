# Controlling-Motors-with-Arduino-UNO
## Table of Contents : 
1. [Introduction](#Introduction)
1. [Servo Motor](#Servo-Motor)
   - [Sweep](#Sweep)
     - [Circuit Components](#Circuit-Components)
     - [Circuit Wiring](#Circuit-Wiring)
     - [Arduino Code](#Arduino-Code)
     - [Code simulation](#Code-simulation)
   - [Knob](#knob)
     - [Circuit Components](#knob-Circuit-Components)
     - [Circuit Wiring](#knob-Circuit-Wiring)
     - [Arduino Code](#knob-Arduino-Code)
     - [Code simulation](#knob-code-simulation)
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

https://github.com/Rawnaa-19/Controlling-Motors-with-Arduino-UNO/assets/106926557/18854ea1-9114-4db4-ba4a-2dafc692e2b4
### knob
Here the servo motor is controlled using an analog potentiometer through the Arduino UNO
#### Knob Circuit Components
1. Arduino UNO
2. Servo motor
3. Potentiometer
4. Wires
5. Breadboard
#### Knob Circuit Wiring 
The servo motor has 3 wires (Vcc , Ground ,and Signal).The Vcc "Red" wire is connected to the 5V pin in the Arduino through the breadboard, the Ground "black" wire is connected to the GND "Ground" pin in the Arduino through the breadboard, and the signal "yellow" wire is connected to pin 9 in the Arduino through the breadboard. And the Potentiometer has 3 wires (Vcc ,Ground ,and Signal "wiper" ).The Vcc "Red" wire is connected to the 5V pin in the Arduino through the breadboard, the Ground "black" wire is connected to the GND "Ground" pin in the Arduino through the breadboard, and the wiper "Orange" wire is connected to the analog pin A0 in the Arduino through the breadboard.<br><br>

<kbd> **Figure 3** <br><br>Servo Motor Knob Circuit <br><br> <kbd>![image](https://github.com/Rawnaa-19/Controlling-Motors-with-Arduino-UNO/assets/106926557/958095c9-5d01-4725-a7cf-203b1f30b3ab)</kbd></kbd>

### Knob Arduino Code
From the Arduino IDE **File>examples>servo>knob** section, a ready to use code is provided.

<kbd>**Figure 4**<br><br>Arduino IDE knob example<br><br> 
<kbd>![image](https://github.com/Rawnaa-19/Controlling-Motors-with-Arduino-UNO/assets/106926557/fc0328da-e6f3-4975-bb8c-87b1002d0ab6)
</kbd></kbd>
<br><br>
The code uses servo library to control the servo motor. It rotates the servo shaft according to the value read from Potentiometer.
```
#include <Servo.h>

Servo myservo;  // create servo object to control a servo

int potpin = A0;  // analog pin used to connect the potentiometer
int val;    // variable to read the value from the analog pin

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  val = analogRead(potpin);            // reads the value of the potentiometer (value between 0 and 1023)
  val = map(val, 0, 1023, 0, 180);     // scale it for use with the servo (value between 0 and 180)
  myservo.write(val);                  // sets the servo position according to the scaled value
  delay(15);                           // waits for the servo to get there
}
```
#### Knob Code simulation


https://github.com/Rawnaa-19/Controlling-Motors-with-Arduino-UNO/assets/106926557/f42b3541-7178-47be-8872-43fbe6515737



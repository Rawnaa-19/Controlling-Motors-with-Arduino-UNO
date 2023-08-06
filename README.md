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
1. [DC Motor](#DC-Motor)
     - [Circuit Components](#DC-Motor-Circuit-Components)
     - [Circuit Wiring](#DC-Motor-Circuit-Wiring)
     - [Arduino Code](#DC-Motor-Arduino-Code)
     - [Code simulation](#knob-Motor-code-simulation)
1. [References](#References)

## Introduction
The second task for the Electronics and Power Department is controlling motors using Arduino UNO. There are two types of motors in this task: servo motors, which rotate 180 degrees, and DC motors, which can move in a clockwise or counterclockwise direction. 
## Servo Motor
The servo motor is an electrical device that rotates machines and robots in an angular direction.[^4]
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
From the Arduino IDE **File>examples>servo>sweep** section, a ready to use code is provided.[^3]

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
From the Arduino IDE **File>examples>servo>knob** section, a ready to use code is provided.[^3]

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

## DC Motor
A DC motor is an electrical device that converts electrical energy into mechanical energy by creating a magnetic field. DC motors operate with motor drivers that control their speed and direction. In this task, the L293D H-bridge is used as the motor driver to control both the speed and direction of two DC motors.[^1]
### DC Motor Circuit Components
1. Arduino UNO
2. Two DC motors
3. L293D H-bridge
4. Wires
5. Breadboard
6. 9v battery
### DC Motor Circuit Wiring
The L293D motor driver has 16 pins.Started with connecting the power pins(pin 8 and pin 16) to the power and the ground pins(pin 4, pin 5,pin 12,and pin 13) to the ground.The first motor "motor A" is connected to the output pins (pin 3 and 6) and the second motor "motor B" is connected to the output pins (pin 11 and 14).Input pins of motor A (pin 2 and 7) is connected to the arduino (pin 4 and 3) respectively.Input pins of motor B (pin 10 and 15) is connected to the arduino (pin 7 and 6) respectively. The enable pin of motor A that control the speed (pin 1) is connected to the arduino (pin 5), and the enable pin of motor B that control the speed (pin 9) is connected to the arduino (pin 8).[^2]<br><br>

<kbd> **Figure 5** <br><br>DC Motor Circuit <br><br> <kbd>![image](https://github.com/Rawnaa-19/Controlling-Motors-with-Arduino-UNO/assets/106926557/5c6b9a15-700e-4c1d-bbe8-eebd3808a761)</kbd></kbd>

### DC Motor Arduino Code
```
// Motor A connections
int enA = 5 ;// yellow wire;
int in1 = 4 ;// blue wire;
int in2 = 3; // purple wire;
// Motor B connections
int enB = 8; // orange wire;
int in3 = 7 ;// pink wire;
int in4 = 6 ;// green wire;

void setup() {
	// Set all the motor control pins to outputs
	pinMode(enA, OUTPUT);
	pinMode(enB, OUTPUT);
	pinMode(in1, OUTPUT);
	pinMode(in2, OUTPUT);
	pinMode(in3, OUTPUT);
	pinMode(in4, OUTPUT);
	
	// Turn off motors - Initial state
	digitalWrite(in1, LOW);
	digitalWrite(in2, LOW);
	digitalWrite(in3, LOW);
	digitalWrite(in4, LOW);
}

void loop() {
	directionControl();
	delay(1000);
	speedControl();
	delay(1000);
}

// This function lets you control spinning direction of motors
void directionControl() {
	// Set motors to maximum speed
	// For PWM maximum possible values are 0 to 255
	analogWrite(enA, 255);
	analogWrite(enB, 255);

	// Turn on motor A & B
	digitalWrite(in1, HIGH);
	digitalWrite(in2, LOW);
	digitalWrite(in3, HIGH);
	digitalWrite(in4, LOW);
	delay(2000);
	
	// Now change motor directions
	digitalWrite(in1, LOW);
	digitalWrite(in2, HIGH);
	digitalWrite(in3, LOW);
	digitalWrite(in4, HIGH);
	delay(2000);
	
	// Turn off motors
	digitalWrite(in1, LOW);
	digitalWrite(in2, LOW);
	digitalWrite(in3, LOW);
	digitalWrite(in4, LOW);
}

// This function lets you control speed of the motors
void speedControl() {
	// Turn on motors
	digitalWrite(in1, LOW);
	digitalWrite(in2, HIGH);
	digitalWrite(in3, LOW);
	digitalWrite(in4, HIGH);
	
	// Accelerate from zero to maximum speed
	for (int i = 0; i < 256; i++) {
		analogWrite(enA, i);
		analogWrite(enB, i);
		delay(20);
	}
	
	// Decelerate from maximum speed to zero
	for (int i = 255; i >= 0; --i) {
		analogWrite(enA, i);
		analogWrite(enB, i);
		delay(20);
	}
	
	// Now turn off motors
	digitalWrite(in1, LOW);
	digitalWrite(in2, LOW);
	digitalWrite(in3, LOW);
	digitalWrite(in4, LOW);
}
```
### knob Motor code simulation


https://github.com/Rawnaa-19/Controlling-Motors-with-Arduino-UNO/assets/106926557/f2dc3658-7581-42e6-a08a-bce654832a9e
## References
[^1]: Agarwal, T. (2021, January 20). DC Motor - Basics, construction, types & its Application. ElProCus - Electronic Projects for Engineering Students. https://www.elprocus.com/dc-motor-basics-types-application/ 
[^2]: Engineers, L. M. (2022, July 21). Control DC Motors with L293D Motor Driver IC & Arduino. Last Minute Engineers. https://lastminuteengineers.com/l293d-dc-motor-arduino-tutorial/ 
[^3]: Servo Motor Basics with Arduino | Arduino Documentation. (n.d.). https://docs.arduino.cc/learn/electronics/servo-motors 
[^4]: The purpose of Servo motors | Fuji Electric Product Column | Fuji Electric Global. (n.d.). https://www.fujielectric.com/products/column/servo/servo_01.html









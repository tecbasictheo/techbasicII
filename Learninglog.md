### 13.10. Lession one

-> Analog does not have clear 0 and 1, it is there more fluid\
-> Basics in Arduino:

- Ontop are global variabls 
- void set up: runs once -> just for the set up
- void looop: runs repataly for the maincode
- void meaning: something is missing -> does not return anything 

- board: board influce how the code is being compiled 
- port: where the input is coming from

#### Project: Lamps

- pins have two modes: input and output 
- HIGH and LOW = 1 and 0\
-> when it is only one, it to fast for us to see the blinking\
-> delay causes us to see the blinking\
-> power from 13 and gnd means 0 
```
void setup() {   // put your setup code here, to run once:
  pinMode(13, OUTPUT);
}

void loop() {   // put your main code here, to run repeatedly:
  digitalWrite(13, HIGH);
  delay(500);
  digitalWrite(13, LOW);
  delay(90);
  digitalWrite(13, HIGH);
  delay(500);
  digitalWrite(13, LOW);
  delay(50);

}
```

### 20.10. Lession two

##### Notes
- Light emitting diode 
- long leg is + 
- Anode is + and kathode is -
- resistors: SMD (surface mount devices) und THT ->  hrough hole tech -> can handel with the eyes and solder by hands

-> color code: for the value 
high power led - phone toarch is one 

- when 5v -> lamp -> 13 = alternated blinking with the board 

- how to power breadboard: Arduino, power supply module, battery power source

Voltage: v volt v\
Current: I Amp A\
Resistance: R Ohm

Resistance is to control the current -> when there is no resistance the lamps draw all the current until they are self destructing  
- current is limiting 
<15mA: safe current for common LEDs 
-> safer to go higer in the resistance

Direct current: DC -> small devices like laptop 
Alternating Current AC: Washing maschine 
- longer more pushing power
  
#### Images
1. circut two lamps bild 
2. parallel circut bild
3. Ampel video

```
const int redLED = 2; 
const int yelLED = 3; 
const int greLED = 4; 

void setup() {   // put your setup code here, to run once:
  pinMode(greLED, OUTPUT);
  pinMode(yelLED, OUTPUT);
  pinMode(redLED, OUTPUT);
}

void loop() {  // put your main code here, to run repeatedly:
  digitalWrite(redLED, HIGH);
  digitalWrite(yelLED, HIGH);
  digitalWrite(greLED, HIGH);
  delay(2000);
  digitalWrite(redLED, LOW);
  digitalWrite(yelLED, LOW);
  digitalWrite(greLED, LOW);
  delay(200);

  digitalWrite(greLED, HIGH);
  delay(200);
  digitalWrite(greLED, LOW);
  delay(200);
  digitalWrite(yelLED, HIGH);
  delay(200);
  digitalWrite(yelLED, LOW);
  delay(200);
  digitalWrite(redLED, HIGH);
  delay(200);
  digitalWrite(redLED, LOW);
  delay(100);

  digitalWrite(redLED, HIGH);
  digitalWrite(yelLED, HIGH);
  digitalWrite(greLED, HIGH);
}
```

The Green LED is dimmer. Lower spectrem of light need less volt to be bright, for example red and yellow. Colors like green, white and blue need more voltage.

```
const int bluLED = 2; 
const int greLED = 3; 
const int redLED = 4; 

void setup() {   // put your setup code here, to run once:
  pinMode(greLED, OUTPUT);
  pinMode(bluLED, OUTPUT);
  pinMode(redLED, OUTPUT);
}

void loop() {  // put your main code here, to run repeatedly:
  digitalWrite(redLED, HIGH);
  digitalWrite(greLED, HIGH);
  digitalWrite(bluLED, HIGH);

  delay(2000);
  digitalWrite(bluLED, LOW);
  digitalWrite(greLED, LOW);
  digitalWrite(redLED, LOW);
  delay(2000);

  digitalWrite(bluLED, HIGH);
  delay(2000);
  digitalWrite(bluLED, LOW);


  digitalWrite(greLED, HIGH);
  delay(2000);
  digitalWrite(greLED, LOW);


  digitalWrite(redLED, HIGH);
  delay(2000);
  digitalWrite(redLED, LOW);

  digitalWrite(bluLED, HIGH);
  digitalWrite(redLED, HIGH);
  delay(2000);
  digitalWrite(bluLED, LOW);
  digitalWrite(redLED, LOW);
  delay(2000);
  digitalWrite(greLED, HIGH);
  digitalWrite(redLED, HIGH);
  delay(2000);
  digitalWrite(greLED, LOW);
  digitalWrite(redLED, LOW);
  delay(2000);
  digitalWrite(greLED, HIGH);
  digitalWrite(bluLED, HIGH);
  delay(2000);
  digitalWrite(greLED, LOW);
  digitalWrite(bluLED, LOW);

}
```
#### analogWrite_

analogWrite_ is in this code used to dim the lights in the lamps. With it, the input of voltage can be controlled. It is used, because the 'digitalWrite' only knows high and low = one and off.

add last video 
```
const int bluLED = 9; 
const int greLED = 10; 
const int redLED = 11; 

void setup() {   // put your setup code here, to run once:
  pinMode(greLED, OUTPUT);
  pinMode(bluLED, OUTPUT);
  pinMode(redLED, OUTPUT);
}

void loop() {  // put your main code here, to run repeatedly:
 setRGB(50,0,0); 
 delay(100);
 setRGB(0,50,0);
 delay(100);
 setRGB(50,50,0);
 delay(2000);
 setRGB(0,50,50);
 delay(2000);
 setRGB(50, 0 ,50);
 delay(2000);

}

void setRGB(int redValue, int greValue, int bluValue){
  analogWrite(redLED, redValue); 
  analogWrite(greLED, greValue); 
  analogWrite(bluLED, bluValue); 


}
```
-> different color values can be used to mix the lamp colors -> different color combination with different lightvalues can create different colored lights.

### 27.10. Lession 3

PWM: Pule-width-modulation 
- digital method of controlling analog power by rapidly switching a signal on and off

Duty-cycle: the proportion of „on-time“ in each cycle 

Code one:\
To fade the light in. 
```
void setup() {   // put your setup code here, to run once:
  pinMode(3, OUTPUT);
}
void loop() {// put your main code here, to run repeatedly:
  for (int i = 0; i <= 255; i += 1) {
    analogWrite(3, i);
    delay(50); 
  }
}
```
Code two:\
To fade in and to fade out: -> video
```
void setup() {   // put your setup code here, to run once:
  pinMode(3, OUTPUT);
}

void loop() {// put your main code here, to run repeatedly:
  for (int i = 0; i <= 255; i += 5) {
    analogWrite(3, i);
    delay(50); 
  }
  for (int i = 255; i >= 0; i -= 5) {
    analogWrite(3, i);
    delay(50); 
  }
}

```
Analog signals are continuous and smooth 
Digital signals are discrete and represented by binary states 

TX(transmit) and  RX(Receive):\
- for serial communication
- usable as normal digital pins, if no serial communication 

- 2-13: Digital I/O pins, ~ for PWM
- A0-5: Analog Input Pins
- VIN: to power the Arduino UNO (7-12V)
- Reset: does the same job as the reset button
- IOREF: Reference Voltage for all I/O pins, connected to 5v on Arduino UNO

digitalWrite() / digitalRead()
HIGH - 5V
Low - 0V
→ Both Digital and Analog Pins

Tilt Switch: detects the tilting of an object

Serial.print()
- serial monitor in tools to open the mointor in Adino

Code three: 
```
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  delay(500);
  Serial.println("Hello");
}

void loop() {
  // put your main code here, to run repeatedly:
  Serial.println("Hello"); 
  delay(10000);
}
```
Code 4: 
With usage of the Tiltsensor: 
```
const int tiltSensor = 2; 
int value = 0; 
void setup() {
  // put your setup code here, to run once:
  pinMode(tiltSensor, INPUT); //like a lamp input 
  Serial.begin(9600);
  delay(500);
}

void loop() {
  value = Serial.println(digitalRead(tiltSensor));
  Serial.println(value);
}
```
Serial Baud Rates: 
- numbers of signal changes per second (serial communication channel)
- The specific rate must be matched between the transmitting and receiving devices .
- commonly used for Arduino: 9600 bps

```
const int tiltSensor = 2; 
int value = 0; 

void setup() {
  // put your setup code here, to run once:
  pinMode(tiltSensor, INPUT_PULLUP); //like a lamp input 
  Serial.begin(9600);
  delay(500);
}

void loop() {
  value = Serial.println(digitalRead(tiltSensor));
  Serial.print("Tilt sensor:"); 
  Serial.println(value);
}
```

INPUT_PULLUP -> foto 
Ask Arduino to use internal pull-up resistors (resistors that connect to power internally)
- Prevents Floating Pins: Without a pull-up or pull-down resistor, an unconnected pin "floats"
- picking up electrical noise and returning random
- unstable HIGH or LOW values.

- digittal read 0 and 1 
- anolog read 0 and 1200 also 5 v only on analog pins 

AnalogRead()
- Analog pin gives you a value between 0 and 1023
- where 0 means 0V and 1023 means the maximum voltage possible (5V by default).
- only use analogRead() on Analog pins

ADC
- Arduino UNO contains a 10-bit, 6-channel analog to digital converter (ADC)
- A device that converts an analog signal (voltage) into a digital value
- You can set the AREF(Analog Reference) pin to sth lower than 5v for higher resolution for low voltage component

Potentiometer
- A potentiometer is an adjustable resistor
- Most common use Case:
Volume Adjustment -> liniar Potentiometer

analog read: 
```
const int pot = A0; 
int value = 0; 

void setup() {
  // put your setup code here, to run once:
  pinMode(A0, INPUT); //like a lamp input 
  Serial.begin(9600);
  delay(500);
}

void loop() {
  value = analogRead(pot);
  Serial.print(„Pot:“);
  Serial.println(value);
}
```

0 means reading 0 volatge - meaning high restisnace 
This makes a volage devider -> is in a serial circle -> share the same voltage they share it 

-   map()
```
const int pot = A0; 
const int led = 3; 
int value = 0; 
int brightness = 0; 

void setup() {
  // put your setup code here, to run once:
  pinMode(A0, INPUT); //like a lamp input 
  pinMode(led, OUTPUT);
  Serial.begin(9600);
  delay(500);
}

void loop() {
  value = analogRead(pot);

  Serial.print("Pot:");
  Serial.println(value);

  brightness = map(value, 0, 1023, 0, 255); 

  analogWrite(led, brightness); 
}
```
brightness control of the lamp -> video und foto 
-> the board connects both actions and do not need to be connected over a cable 

photorestiser: reconises when something is over it and/or covering it

```
const int pot = A0; 
const int led = 3; 
int value = 0; 
int brightness = 0; 

void setup() {
  // put your setup code here, to run once:
  pinMode(A0, INPUT); //like a lamp input 
  pinMode(led, INPUT);
  Serial.begin(9600);
  delay(500);
}

void loop() {
  value = analogRead(pot);

  Serial.print("Pot:");
  Serial.println(value);

  brightness = map(value, 0, 1023, 0, 255); 

  analogWrite(led, brightness); 
}

```
photo mit sensor -> need 10k resistor 
touch lamp video

```
const int pot = A0; 
const int led = 3; 
int value = 0; 
int brightness = 0; 

void setup() {
  // put your setup code here, to run once:
  pinMode(A0, INPUT); //like a lamp input 
  pinMode(led, INPUT);
  Serial.begin(9600);
  delay(500);
}

void loop() {
  value = analogRead(pot);

  Serial.print("Pot:");
  Serial.println(value);

  if (value > 400) {
    digitalWrite(led, LOW); 
  } else {
    digitalWrite(led, HIGH); 
  }
}
```

 


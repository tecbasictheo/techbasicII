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


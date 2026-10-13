### 13.10. Lession one

-> Analog does not have clear 0 and 1, it is there more fluid\
-> Basics in Arduino:

Ontop are global variabls 
void set up: runs once -> just for the set up 
void looop: runs repataly for the maincode 
void meaning: something is missing -> does not return anything 

- board: board influce how the code is being compiled 
- port: where the input is coming from

####Project: Lamps
- pins have two modes: input and output 
- HIGH and LOW = 1 and 0 
-> when it is only one, it to fast for us to see the blinking 
-> delay causes us to see the blinking
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



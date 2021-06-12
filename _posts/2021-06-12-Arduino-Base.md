---
published: true
---
## My second arduino board kit

Bought this [https://www.aliexpress.com/item/4001107780551.html](https://www.aliexpress.com/item/4001107780551.html )

And experimented a bit:
[https://pastebin.com/G3L1uD2Y](https://pastebin.com/G3L1uD2Y) 

### DISPLAYING SENSOR DATA CUSTOMIZED!
![](https://i.ibb.co/FsDVBKn/IMG-20210605-210844.jpg)

[https://www.circuitbasics.com/arduino-7-segment-display-tutorial/](https://www.circuitbasics.com/arduino-7-segment-display-tutorial/)
[https://www.makerguides.com/lm35-arduino-tutorial/](https://www.makerguides.com/lm35-arduino-tutorial/)



                #define sensorPin A0
                #include <SevSeg.h>
                  int digitBuffer[4] = { 0};
                SevSeg sevseg; //Instantiate a seven segment controller object

                unsigned long previousMillis = 0;
                const long interval = 1000;
                int i, j, k;

                void setup()
                {
                  byte numDigits = 4;
                  byte digitPins[] = {10, 11, 12, 13};
                  byte segmentPins[] = {9, 2, 3, 5, 6, 8, 7, 4};

                  sevseg.begin(COMMON_ANODE, numDigits, digitPins, segmentPins);
                  sevseg.setBrightness(10);
                  //Serial.begin(9600);

                }

                void loop()
                {


                  int reading = analogRead(sensorPin);
                  float tempC = reading * (5000 / 1024.0) / 10;


                  /*unsigned long timerGlobal = millis();
                  sevseg.setNumber(timerGlobal/1000);  
                  sevseg.refreshDisplay();*/

                  static unsigned long timer = millis();
                  if (millis() >= timer) {
                    timer += 300;
                    sevseg.setNumber(tempC, 2);
                  }

                  sevseg.refreshDisplay();
                  /*Serial.print(tempC);
                  Serial.print(" \xC2\xB0"); // shows degree symbol
                  Serial.println("C");
                  delay(1000);*/


                }
 

### WATER SENSOR
[https://arduinogetstarted.com/tutorials/arduino-water-sensor](https://arduinogetstarted.com/tutorials/arduino-water-sensor)

### STEPPER MOTOR BIG
[https://youtu.be/avrdDZD7qEQ](https://youtu.be/avrdDZD7qEQ)
[https://www.lombardoandrea.com/motori-passo-passo-arduino-joystick/](https://www.lombardoandrea.com/motori-passo-passo-arduino-joystick/)

### SG90 MICRO SERVER
[https://www.youtube.com/watch?v=ceTYMgdfhRk](https://www.youtube.com/watch?v=ceTYMgdfhRk)

### STEPPER MOTOR WITH JOYSTICK
![](https://i.ibb.co/fSGm1v1/IMG-20210608-213447.jpg)

[https://simple-circuit.com/arduino-stepper-motor-joystick-control/](https://simple-circuit.com/arduino-stepper-motor-joystick-control/)
[https://create.arduino.cc/projecthub/arduino-applications/stepper-motor-control-with-joystick-f5feb1](https://create.arduino.cc/projecthub/arduino-applications/stepper-motor-control-with-joystick-f5feb1)
 
                int s1 = 2;
                int s2 = 3;
                int s3 = 4;
                int s4 = 5;
                int x;
                void setup() {
                  pinMode(s1, OUTPUT);
                  pinMode(s2, OUTPUT);
                  pinMode(s3, OUTPUT);
                  pinMode(s4, OUTPUT);
                  pinMode(A4, INPUT);
                 }
                void loop() {
                  x = analogRead(A4);
 
                  if(x<500)
                  {
                 digitalWrite(s1, HIGH);
                 digitalWrite(s2, LOW);
                 digitalWrite(s3, LOW);
                 digitalWrite(s4, LOW);
                 delay(5);
                 digitalWrite(s1, LOW);
                 digitalWrite(s2, HIGH);
                 digitalWrite(s3, LOW);
                 digitalWrite(s4, LOW);
                 delay(5);
                 digitalWrite(s1, LOW);
                 digitalWrite(s2, LOW);
                 digitalWrite(s3, HIGH);
                 digitalWrite(s4, LOW);
                 delay(5);
                 digitalWrite(s1, LOW);
                 digitalWrite(s2, LOW);
                 digitalWrite(s3, LOW);
                 digitalWrite(s4, HIGH);
                 delay(5);
                 }
                 else if(x>550)
                 {
                  digitalWrite(s1, LOW);
                 digitalWrite(s2, LOW);
                 digitalWrite(s3, LOW);
                 digitalWrite(s4, HIGH);
                 delay(5);
                 digitalWrite(s1, LOW);
                 digitalWrite(s2, LOW);
                 digitalWrite(s3, HIGH);
                 digitalWrite(s4, LOW);
                 delay(5);
                 digitalWrite(s1, LOW);
                 digitalWrite(s2, HIGH);
                 digitalWrite(s3, LOW);
                 digitalWrite(s4, LOW);
                 delay(5);
                 digitalWrite(s1, HIGH);
                 digitalWrite(s2, LOW);
                 digitalWrite(s3, LOW);
                 digitalWrite(s4, LOW);
                 delay(5);
                 }
                 else if(x > 500 && x < 550)
                 {
                 digitalWrite(s1, LOW);
                 digitalWrite(s2, LOW);
                 digitalWrite(s3, LOW);
                 digitalWrite(s4, LOW);
                 }
                }
 


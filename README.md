# Internet_of_things


**led blink**:
https://wokwi.com/projects/333797046452486740

https://wokwi.com/projects/333798376274395731


https://wokwi.com/projects/333800084416234068
{
  "version": 1,
  "author": "Anonymous maker",
  "editor": "wokwi",
  "parts": [
    { "type": "wokwi-arduino-uno", "id": "uno", "top": 0, "left": 0, "attrs": {} },
    {
      "type": "wokwi-resistor",
      "id": "r1",
      "top": -133.05,
      "left": 151.91,
      "attrs": { "value": "1000" }
    },
    {
      "type": "wokwi-resistor",
      "id": "r2",
      "top": -108.73,
      "left": 152.93,
      "attrs": { "value": "1000" }
    },
    {
      "type": "wokwi-resistor",
      "id": "r3",
      "top": -80.68,
      "left": 153.01,
      "attrs": { "value": "1000" }
    },
    { "type": "wokwi-rgb-led", "id": "rgb1", "top": -230.37, "left": 80.37, "attrs": {} }
  ],
  "connections": [
    [ "rgb1:COM", "uno:5V", "green", [ "v1.48", "h240.57", "v379.07", "h-176.84", "v1.88" ] ],
    [ "rgb1:R", "r1:1", "green", [ "v3.01", "h-65.54", "v65.84" ] ],
    [ "rgb1:G", "r2:1", "green", [ "v34.76", "h-150.22", "v58.32" ] ],
    [ "rgb1:B", "r3:1", "green", [ "v50.1", "h-217.84", "v64.9" ] ],
    [ "r3:2", "uno:11", "green", [ "v1.2", "h32.37", "v45.15", "h-101.59" ] ],
    [ "r2:2", "uno:10", "green", [ "v-0.85", "h54.08", "v88.42", "h-114.76" ] ],
    [ "r1:2", "uno:9", "green", [ "v1.83", "h67.33", "v115.7", "h-113.82" ] ]
  ]
}

https://wokwi.com/projects/333806282102276690

**temperature and humidity sensor:**<br>
https://wokwi.com/projects/334432657132749396

**ultrasonic sensor:**<br>
https://wokwi.com/projects/334433287459045970

**infrared sensor:**<br>
https://wokwi.com/projects/334434444877234771

**pir sensor:**<br>
https://wokwi.com/projects/334434753049526866

**led fade:**<br>
https://wokwi.com/projects/334435448281629266

**led button:**<br>
https://wokwi.com/projects/334435795295273554

**motion sensor:**<br>
https://wokwi.com/projects/334436116397556306

**motion sensor with led:**<br>
https://wokwi.com/projects/334436693137424978

**motion sensor with buzzer:**<br>
https://wokwi.com/projects/334437025681769044

**ultrasonic buzzer:**<br>
https://wokwi.com/projects/334434213071684180

**ultrasonic led:**<br>
https://wokwi.com/projects/334437975813259860

**servomotor:**<br>
https://wokwi.com/projects/335065632001229394

**serovo motor controlled by potentiometer:**<br>
https://wokwi.com/projects/335066301261152851

**button servo motor:**<br>
https://wokwi.com/projects/335066627366191698

**servo motor using ultrasonic:**<br>
https://wokwi.com/projects/335066953225863762

**buzzer beep:**<br>
https://wokwi.com/projects/335071019023729236

**buzzer beep using pushbutton:**<br>
https://wokwi.com/projects/335067666141151828

**ultrasonic buzzer with led**<br>
https://wokwi.com/projects/335613901308691027

**Lcd**:<br>
https://wokwi.com/projects/333806073021465171

**potentiometer fade led**:<br>
https://wokwi.com/projects/335700946921194068

**lablist 1**<br>
https://wokwi.com/projects/338148645122605652

**lablist 1 with esp32**<br>
https://wokwi.com/projects/338225981441442386

**lablist2**<br>
https://wokwi.com/projects/337602684471214674

** IR sensor**:
**HARDWARE**<br>
**IR SENSOR**<br>
int ir=D5;<br>
int led=D6;
void setup() {<br>
  // put your setup code here, to run once:<br>
  pinMode(ir,INPUT);<br>
    pinMode(led,OUTPUT);<br>
    Serial.begin(9600);<br>
    
}<br>

void loop() {<br>
  // put your main code here, to run repeatedly:<br>
  int irvalue=digitalRead(ir);<br>
  if(irvalue==LOW)<br>
  {<br>
    Serial.println("LOW");<br>
    digitalWrite(led,HIGH);<br>
  }<br>
  else<br>
  {<br>
    Serial.println("HIGH");<br>
    digitalWrite(led,LOW);<br>
  }<br>
delay(100);<br>
}<br>

**flood monitering system**<br>
#include "ThingSpeak.h"<br>
#include <ESP8266WiFi.h><br>
const int trigPin1 = D6;<br>
const int echoPin1 = D7;<br>
#define redled D2<br>
#define grnled D4<br>
#define BUZZER D1 //buzzer pin <br>
unsigned long ch_no = 1053193;//Replace with Thingspeak Channel number<br>
const char * write_api = "8JQGAAUOIA12K2MD";//Replace with Thingspeak write API<br>
char auth[] = "mwa0000027193738";<br>
char ssid[] = "OPPO A3s";<br>
char pass[] = "vanithavvj";<br>
unsigned long startMillis;<br>
unsigned long currentMillis;<br>
const unsigned long period = 10000;<br>
WiFiClient client;<br>
long duration1;<br>
int distance1;<br>
void setup() {<br>
pinMode(trigPin1, OUTPUT);<br>
pinMode(echoPin1, INPUT);<br>
pinMode(redled, OUTPUT);<br>
pinMode(grnled, OUTPUT);<br>
digitalWrite(redled, LOW);<br>
digitalWrite(grnled, LOW);<br>
Serial.begin(115200);<br>
WiFi.begin(ssid, pass);<br>
while (WiFi.status() != WL_CONNECTED)<br>
{<br>
delay(1000);<br>
Serial.print(".");<br>
Serial.println("WiFi co<br>nnected");<br>
Serial.println(WiFi.localIP());<br>
ThingSpeak.begin(client);<br>
startMillis = millis(); //initial start time<br>
}<br>
void loop()<br>
{<br>
digitalWrite(trigPin1, LOW);<br>
delayMicroseconds(2);<br>
digitalWrite(trigPin1, HIGH);<br>
delayMicroseconds(10);<br>
digitalWrite(trigPin1, LOW);<br>
duration1 = pulseIn(echoPin1, HIGH);<br>
distance1 = duration1 * 0.034 / 2;<br>
Serial.println(distance1);<br>
if (distance1 <= 400)<br>
{<br>
digitalWrite(D2, HIGH);<br>
tone(BUZZER, 300);<br>
digitalWrite(D4, LOW);<br>
delay(1500);<br>
noTone(BUZZER);<br>
}<br>
else<br>
{<br>
digitalWrite(D4, HIGH);<br>
digitalWrite(D2, LOW);<br>
}<br>
currentMillis = millis();<br>
if (currentMillis - startMillis >= period)<br>
{<br>
ThingSpeak.setField(1, distance1);<br>
ThingSpeak.writeFields(ch_no, write_api);<br>
startMillis = currentMillis;<br>
}<br>
}<br>

**LED series**<br>

int pinsCount=5; // declaring the integer variable pinsCount<br>
int pins[] = {D1,D2,D3,D4,D5,}; // declaring the array pins[]<br>

void setup() {<br>
for (int i=0; i<pinsCount; i=i+1){ // counting the variable i from 0 to 9<br>
pinMode(pins[i], OUTPUT); // initialising the pin at index i of the array of pins as OUTPUT<br>
}<br>
}<br>
void loop() {<br>
for (int i=0; i<pinsCount; i=i+1){ // chasing right<br>
digitalWrite(pins[i], HIGH); // switching the LED at index i on<br>
delay(100); // stopping the program for 100 milliseconds<br>
digitalWrite(pins[i], LOW); // switching the LED at index i off<br>
}<br>
for (int i=pinsCount-1; i>0; i=i-1){ // chasing left (except the outer leds)<br>
digitalWrite(pins[i], HIGH); // switching the LED at index i on<br>
delay(100); // stopping the program for 100 milliseconds<br>
digitalWrite(pins[i], LOW); // switching the LED at index i off<br>

}<br>
}<br>


**Seven segment LED display:**<br>
https://wokwi.com/projects/342585695001379411<br>

**Analog Joystick with two axes (horizontal/vertical) and an integrated push button. Etch-a-sketch - A simple drawing game using a MAX7219 LED Dot Matrix Reference:**<br>
https://wokwi.com/projects/342586850013086290<br>

**DHT22 on the ESP32 Reference**<br>
https://wokwi.com/projects/342587624374927954<br>

**Display distance on LCD screen with buzzer and LED  Reference 1:**<br>
https://wokwi.com/projects/342589400784306771<br>

https://wokwi.com/projects/342590121552380499<br>

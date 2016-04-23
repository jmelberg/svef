## Distance Sensor

#### Tutorial by [Instructables](http://www.instructables.com/id/Arduino-Distance-Detector-with-a-Buzzer-and-LEDs/?ALLSTEPS)

#### Parts:
* 1 Breadboard
* 1 Arduino
* 6+ Jumper Wires
* 1 Ultrasonic Sensor
* Buzzer (Optional)
* LEDs (Optional)
* Resistors (1 per LED)

#### Setup:
***
![Breadboard - Arduino]
(http://cdn.instructables.com/FBN/QVIF/HJA2EJX2/FBNQVIFHJA2EJX2.MEDIUM.jpg)

* Ultrasonic
  * Echo -> Pin 6
  * Trig -> Pin 7
* Buzzer (Optional)
  * Pin 3
* LEDs
  * LED 1 -> Pin 8
  * LED 2 -> Pin 9
  * LED 3 -> Pin 10
  * LED 4 -> Pin 11
  * LED 5 -> Pin 12

#### Code:
***
``` c++
/*
  Code provided by Instructables.com
  User: flynn_munroe
*/
// Define Pins and Buzzer
#define trigPin 7
#define echoPin 6
#define led 13
#define led2 12
#define led3 11
#define led4 10
#define led5 9
#define led6 8
#define buzzer 3

// Piezo
int sound = 250;

void setup() {
  Serial.begin (9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(led, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
  pinMode(led4, OUTPUT);
  pinMode(led5, OUTPUT);
  pinMode(led6, OUTPUT);
  pinMode(buzzer, OUTPUT);
}

void loop() {
  long duration, distance;
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = (duration/2) / 29.1;

  if (distance <= 30) {
    digitalWrite(led, HIGH);
    sound = 250;
}
  else {
    digitalWrite(led,LOW);
  }
  if (distance < 25) {
      digitalWrite(led2, HIGH);
      sound = 260;
}
  else {
      digitalWrite(led2, LOW);
  }
  if (distance < 20) {
      digitalWrite(led3, HIGH);
      sound = 270;
} 
  else {
    digitalWrite(led3, LOW);
  }
  if (distance < 15) {
    digitalWrite(led4, HIGH);
    sound = 280;
}
  else {
    digitalWrite(led4,LOW);
  }
  if (distance < 10) {
    digitalWrite(led5, HIGH);
    sound = 290;
}
  else {
    digitalWrite(led5,LOW);
  }
  if (distance < 5) {
    digitalWrite(led6, HIGH);
    sound = 300;
}
  else {
    digitalWrite(led6,LOW);
  }
 
  if (distance > 30 || distance <= 0){
    Serial.println("Out of range");
    noTone(buzzer);
  }
  else {
    Serial.print(distance);
    Serial.println(" cm");
    tone(buzzer, sound);
  }
  delay(500);
}

```

## Force Sensor

#### Tutorial by [Instructables](http://www.instructables.com/id/How-to-use-a-Force-Sensitive-Resistor-Arduino-Tuto/?ALLSTEPS)
#### Parts:
* 1 Breadboard
* 1 Arduino
* 1 Force Sensitive Resistor
* 6 Jumper Wires
* 1 10K Ohm Resistor
* 1 220 Ohm Resistor

#### Setup:
***
![Arduino to Breadboard]
(http://cdn.instructables.com/FOT/PUUB/IEV84N5O/FOTPUUBIEV84N5O.MEDIUM.jpg)

#### Code:
***
``` c++
/* How to use a Force sensitive resistor to fade an LED with Arduino
   Dev: Michalis Vasilakis // Date: 22/9/2015 // www.ardumotive.com
*/

//Constants:
const int ledPin = 3;     //pin 3 has PWM funtion
const int sensorPin = A0; //pin A0 to read analog input

//Variables:
int value; //save analog value

void setup(){
  pinMode(ledPin, OUTPUT);  //Set pin 3 as 'output' 
  Serial.begin(9600);       //Begin serial communication
}

void loop(){
  value = analogRead(sensorPin);       //Read and save analog value from potentiometer
  Serial.println(value);               //Print value
  value = map(value, 0, 1023, 0, 255); //Map value 0-1023 to 0-255 (PWM)
  analogWrite(ledPin, value);          //Send PWM value to led
  delay(100);                          //Small delay
}
```

## Alcohol Sensor

#### Tutorial by [bildr.org](http://bildr.org/2013/10/mq3-arduino/)
#### Parts:
* 1 Breadboard
* 1 Arduino
* Jumper Wires
* 1 10K Ohm Resistor
* 1 MQ-3 Sensor

#### Setup:
***
![Arduino to Breadboard]
(http://bildr.org/blog/wp-content/uploads/2013/10/mq3-arduino-hookup-400x219.png)

#### Code:
***
``` c++
int mq3_analogPin = A0; // connected to the output pin of MQ3 

void setup(){
  Serial.begin(9600); // open serial at 9600 bps
}

void loop()
{
  // give ample warmup time for readings to stabilize

  int mq3_value = analogRead(mq3_analogPin);
  Serial.println(mq3_value);

  delay(100); //Just here to slow down the output.
}
```

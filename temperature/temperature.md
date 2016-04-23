## Temperature Sensor

#### Tutorial by [SparkFun](https://learn.sparkfun.com/tutorials/sik-experiment-guide-for-arduino---v32/experiment-7-reading-a-temperature-sensor)

#### Parts:
* 1 Breadboard
* 1 Arduino
* 5 Jumper Wires
* 1 Temperature Sensor

#### Setup:
***
![Arduino to Breadboard]
(https://cdn.sparkfun.com/r/600-600/assets/learn_tutorials/3/1/0/Arduino_circuit_07_01.png)

#### Temperature Sensor:
***
![Front Temp Sensor]
(https://cdn.sparkfun.com/r/600-600/assets/learn_tutorials/2/7/5/TMP_pinout_drawing.png)

#### Code:
***
``` c++
/*
SparkFun Inventor's Kit 
Version 2.0 6/2012 MDG
*/

// We'll use analog input 0 to measure the temperature sensor's signal pin.

const int temperaturePin = 0;

void setup()
{
  // Use the Arduino's serial port
  
  // The speed is measured in bits per second, also known as
  // "baud rate". 9600 is a very commonly used baud rate,
  // and will transfer about 10 characters per second.

  Serial.begin(9600);
}

void loop()
{
  float voltage, degreesC, degreesF;
  
  // Get current voltage
  voltage = getVoltage(temperaturePin);

  // Now we'll convert the voltage to degrees Celsius.
  degreesC = (voltage - 0.5) * 100.0;

  // This is the classic C to F conversion formula:
  degreesF = degreesC * (9.0/5.0) + 32.0;

  // Test the data
  Serial.print("voltage: ");
  Serial.print(voltage);
  Serial.print("  deg C: ");
  Serial.print(degreesC);
  Serial.print("  deg F: ");
  Serial.println(degreesF);

  delay(1000); // repeat once per second (change as you wish!)
}

float getVoltage(int pin)
{
  // This function has one input parameter, the analog pin number
  // to read. You might notice that this function does not have
  // "void" in front of it; this is because it returns a floating-
  // point value, which is the true voltage on that pin (0 to 5V).

  return (analogRead(pin) * 0.004882814);

  // This equation converts the 0 to 1023 value that analogRead()
  // returns, into a 0.0 to 5.0 value that is the true voltage
  // being read at that pin.
}
```

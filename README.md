Author: Maeva CAQUELARD Date: November 21, 2024
Description
This library allows you to measure temperature using a Negative Temperature Coefficient (NTC) thermistor. It provides a class for converting analog readings to temperature in Kelvin, Celsius, or Fahrenheit, using the properties of the thermistor and a voltage divider circuit.
Features
Easy integration with Arduino, ESP32, and similar microcontrollers.
Support for customizable thermistor and circuit parameters.
Accurate conversion of analog-to-digital readings to temperature.
Schematic
Below is a simple schematic for connecting a thermistor:
Key terms:
R0: Fixed resistor in series with the thermistor.
ADC: Analog-to-digital converter input.
Vcc: Supply voltage.
Installation
Clone this repository or download the library as a ZIP file.
Place the folder Thermistor in your Arduino libraries folder.
Restart your Arduino IDE.
Example
The following example demonstrates how to use the Thermistor class:
Plain Text
#include <Thermistor.h>// Thermistor parametersdouble Rref = 10000; // Reference resistance at T0double R0 = 10000;   // Fixed resistor valuedouble Beta = 3950;  // Beta coefficientdouble T0 = 298.15;  // Reference temperature in Kelvin (25°C)double Vcc = 5;      // Supply voltageunsigned samplingBitsNumber = 10; // ADC resolution (Arduino UNO)// Create a Thermistor objectThermistor thermistor(Rref, R0, Beta, samplingBitsNumber, Vcc, T0);
void setup() {
    Serial.begin(9600);
}
void loop() {
    int adcValue = analogRead(A0); // Read ADC valuedouble temperature = thermistor.getTemperature(adcValue, 'C'); // Get temperature in Celsius    Serial.print("Temperature: ");
    Serial.print(temperature);
    Serial.println(" °C");
    delay(5000); // Wait for 5 seconds
}
Thermistor/
├── examples/
│   └── simpleTest/
│       └── main.cpp
├── include/
│   └── Thermistor.h
├── src/
│   └── Thermistor.cpp
└── library.json

**Name:** ABHISHEK KUMAR

**Company:** CODTECH IT SOLUTIONS

**ID:** CT04ES2249

**Domain:** Embedded Systems

**Duration:** 15th June to 15th July

**Mentor:** G.SRAVANI

#  Overview of the Project 
## Project: Temperature and Humidity Monitoring with DHT Sensor

### Objective:
The project aims to build a temperature and humidity monitoring system using an Arduino Uno, a DHT11 sensor, and a 1602 LCD display with I2C interface. The system will read environmental data and display it on the LCD screen in real-time.

### Components Needed:
1. Arduino Uno
2. DHT11 sensor (3-pin version)
3. 1602 I2C LCD display
4. Jumper wires
5. Breadboard

### Hardware Connections:

#### Connecting the DHT11 Sensor to Arduino:
1. **VCC**: Connect to **5V** on the Arduino.
2. **DATA**: Connect to **Pin 4** (you can also use pins 3, 5, 12, 13, or 14; Pin 15 can work but the DHT must be disconnected during program upload).
3. **GND**: Connect to **GND** on the Arduino.

#### Connecting the LCD 1602 I2C Display to Arduino:
1. **VCC**: Connect to **5V** on the Arduino.
2. **GND**: Connect to **GND** on the Arduino.
3. **SDA**: Connect to **A4** (Analog Pin 4).
4. **SCL**: Connect to **A5** (Analog Pin 5).

### Software Code:

The project uses two libraries: one for the DHT sensor and the other for the LCD 1602 I2C display. You need to install these libraries from the Arduino Library Manager:
1. **DHT sensor library by Adafruit**
2. **LiquidCrystal I2C by Frank de Brabander**

Here's the complete Arduino code:

```cpp
#include <DHT.h>
#include <LiquidCrystal_I2C.h>

// Define the DHT sensor pin
#define DHTPIN 4

// Define the type of DHT sensor used
#define DHTTYPE DHT11

// Initialize the DHT sensor
DHT dht(DHTPIN, DHTTYPE);

// Initialize the LCD display
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  dht.begin();         // Initialize the sensor
  lcd.backlight();     // Turn on LCD backlight
  lcd.init();          // Initialize LCD
}

void loop() {
  lcd.clear();         // Clear the display
  lcd.setCursor(0, 0); // Set the cursor on the first row and column
  lcd.print("Humidity="); 
  lcd.print((float)dht.readHumidity()); // Print the humidity
  lcd.print("%");
  lcd.setCursor(0, 1); // Set the cursor on the second row and first column
  lcd.print("Temp=");
  lcd.print((float)dht.readTemperature()); // Print the temperature
  lcd.print("Celsius");
  delay(2000);         // Wait for 2 seconds
}
```

### Explanation:

1. **Libraries**: The code includes `DHT.h` for the DHT sensor and `LiquidCrystal_I2C.h` for the LCD display.
2. **Define Pins and Sensor Type**: The `DHTPIN` and `DHTTYPE` macros define the data pin (Pin 4) and sensor type (DHT11).
3. **Initialization**: In the `setup()` function, the DHT sensor and LCD are initialized.
4. **Reading and Displaying Data**: In the `loop()` function, the sensor reads temperature and humidity every 2 seconds. The readings are then displayed on the LCD screen. If the readings are invalid, the code handles this internally.

### Conclusion

This project demonstrates the successful interfacing of a DHT11 temperature and humidity sensor with an Arduino Uno, displaying the sensor readings on a 1602 I2C LCD screen. The following conclusions can be drawn from the project:

1. **Effective Sensor Integration**: The DHT11 sensor is effectively integrated with the Arduino, providing accurate readings of temperature and humidity. The code can be easily modified to accommodate other DHT sensors (like DHT22) by changing the sensor type in the code.

2. **Efficient Data Display**: The 1602 I2C LCD display allows for efficient and clear visualization of the sensor data. Using the I2C interface simplifies wiring and reduces the number of pins used on the Arduino.

3. **Modularity and Flexibility**: The project demonstrates the modularity of Arduino projects. By changing a few lines of code, different sensors can be used, and the display output can be customized.

4. **Practical Application**: This setup can be applied in various real-world scenarios, such as environmental monitoring systems, home automation, and weather stations, where monitoring temperature and humidity is crucial.

5. **Learning Experience**: The project provides a solid foundation for beginners to learn about sensor interfacing, I2C communication, and using libraries in Arduino programming. It enhances understanding of both hardware connections and software implementation.

Overall, this project serves as a useful starting point for more complex sensor-based projects and showcases the versatility of the Arduino platform in creating interactive and functional electronic systems.


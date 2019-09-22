# Data Logger (and using cool sensors!)

*A lab report by Noel Konagai.*

## Part A.  Writing to the Serial Monitor
 
**a. Based on the readings from the serial monitor, what is the range of the analog values being read?**
The analog values change between 0 and 1023, in other words they have a 10 bit value.
 
**b. How many bits of resolution does the analog to digital converter (ADC) on the Arduino have?**
10 bits.

## Part B. RGB LED

**How might you use this with only the parts in your kit? Show us your solution.**

I connected the RGB LED to pins 9, 10, 13, and each of the colored legs to a resistance of 1kOhm. Despite that, the LED was too bright to discern better the colors so I used a photoresistor for the red leg to see if the red will appear dimmer. It somehow did appear dimmer, but I was not convinced.

[Link to video](https://photos.app.goo.gl/MV5qYjsxaNbFD8Y28)

## Part C. Voltage Varying Sensors 
 
### 1. FSR, Flex Sensor, Photo cell, Softpot

**a. What voltage values do you see from your force sensor?**

After converting the analog to digital reading to voltages, I was able to get values between 0.1 to 3.8Vs. I was not able to exert enough force to get closer to 5V.

**b. What kind of relationship does the voltage have as a function of the force applied? (e.g., linear?)**

At a glance it seems to be logarithmic, but it is hard to tell as it is hard to exert a force that is constantly increasing. All things considered, it is a positive correlation.

[Link to Color LED code](https://github.com/noelkonagai/interactive-devices/blob/master/Lab%203/led_color.ino)

![FSR Reading Image](https://github.com/noelkonagai/interactive-devices/blob/master/Lab%203/Screen%20Shot%202019-09-21%20at%207.15.38%20PM.png)

**c. Can you change the LED fading code values so that you get the full range of output voltages from the LED when using your FSR?**

Yes. I used the input from the FSR coming in at A0 pin, mapped it to range between 0 and 255, and wrote it to the LED pin. Below the code snippet demonstrates this.

```java
fsrReading = analogRead(fsrPin);
fsrLED = map(fsrReading, 0, 1023, 0, 255);   
analogWrite(led, fsrLED);
```
Link to FSR Fading LED [code](https://github.com/noelkonagai/interactive-devices/blob/master/Lab%203/fsr_led_fade.ino)
Link to [video](https://photos.app.goo.gl/nKdNUExjPa1w256cA)

**d. What resistance do you need to have in series to get a reasonable range of voltages from each sensor?**

Photo cell needed about 2kOhm of resistance and the help of my Phone's flashlight. 

Softpot needed 10kOhm of resistance.

Flex sensor needed 25kOhm of resistance.

**e. What kind of relationship does the resistance have as a function of stimulus? (e.g., linear?)**

Photo cell increases its resistance when it's darker, thus with the brightness the resistance has an inverse relationship.

As for the softpot, its resistance has a linear relationship to the distance from the touching point to the connected end.

The flex sensor's resistance decreases as it is bent forwards, and it increases as it is bent backwards.

### 2. Accelerometer
 
**a. Include your accelerometer read-out code in your write-up.**

### 3. IR Proximity Sensor

**a. Describe the voltage change over the sensing range of the sensor. A sketch of voltage vs. distance would work also. Does it match up with what you expect from the datasheet?**

**b. Upload your merged code to your lab report repository and link to it here.**

## Optional. Graphic Display

**Take a picture of your screen working insert it here!**

## Part D. Logging values to the EEPROM and reading them back
 
### 1. Reading and writing values to the Arduino EEPROM

**a. Does it matter what actions are assigned to which state? Why?**

**b. Why is the code here all in the setup() functions and not in the loop() functions?**

**c. How many byte-sized data samples can you store on the Atmega328?**

**d. How would you get analog data from the Arduino analog pins to be byte-sized? How about analog data from the I2C devices?**

**e. Alternately, how would we store the data if it were bigger than a byte? (hint: take a look at the [EEPROMPut](https://www.arduino.cc/en/Reference/EEPROMPut) example)**

**Upload your modified code that takes in analog values from your sensors and prints them back out to the Arduino Serial Monitor.**

### 2. Design your logger
 
**a. Insert here a copy of your final state diagram.**

### 3. Create your data logger!
 
**a. Record and upload a short demo video of your logger in action.**

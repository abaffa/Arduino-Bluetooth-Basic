# Arduino-Bluetooth-Basic
Control a LED using your smartphone via bluetooth
Download the app from here : http://goo.gl/PSXVoF
Website : https://igniteinnovateideas.wordpress.com

---

Ever thought of controlling any electronic devices with your smart phone ?Controlling your robot or any other devices with your smartphone will be really cool. Here is is a simple and basic tutorial for interfacing Bluetooth with arduino

### Things you need
#### Hardware
1. Bluetooth Module HC 05/06
2. Arduino
3. LED
4. 220Ω Resistor
5. Android device

![Schema](https://igniteinnovateideas.files.wordpress.com/2016/04/thing-u-need.png?w=335&h=340)

### Thing u need
#### Software
1. Arduino IDE
2. Android Studio (Not Really required I will  provide the android application :D)

### Watch how does it works ?
###### Watch the video tutorial

[![Tutorial](http://img.youtube.com/vi/azxshrFSgnA/0.jpg)](http://www.youtube.com/watch?v=azxshrFSgnA)
 
![good](https://igniteinnovateideas.files.wordpress.com/2016/04/good.gif?w=535&zoom=2)

### Let’s Start Building
The circuit is so simple and small , there is only few connection to be made

Arduino Pins           Bluetooth Pins

RX (Pin 0)     ———->      TX
TX (Pin 1)     ———->      RX
5V             ———->      VCC
GND            ———->      GND

Connect a LED negative to GND of arduino and positive to pin 13 with a resistance valued between 220Ω – 1KΩ. And your done with the circuit

**Note : Don’t  Connect RX to RX and TX to TX of Bluetooth to arduino you will receive no data , Here TX means Transmit and RX means Receive**

![hc-05-LED blink Circuit](https://igniteinnovateideas.files.wordpress.com/2016/04/hc-05-led-blink-circuit.png?w=768&h=1149)

### Upload the Code
```C
/*
* Bluetooh Basic: LED ON OFF - Avishkar
* Coder - Mayoogh Girish
* Website - http://bit.do/Avishkar
* Download the App : https://github.com/Mayoogh/Arduino-Bluetooth-Basic
* This program lets you to control a LED on pin 13 of arduino using a bluetooth module
*/
char data = 0; //Variable for storing received data
void setup()
{
    Serial.begin(9600); //Sets the baud for serial data transmission                               
    pinMode(13, OUTPUT); //Sets digital pin 13 as output pin
}
void loop()
{
   if(Serial.available() > 0)  // Send data only when you receive data:
   {
      data = Serial.read();        //Read the  incoming  data and store it into variable data
      Serial.print(data);          //Print Value inside data in Serial monitor
      if(data == '1')              // Checks whether value of data is equal to 1
         digitalWrite(13, HIGH);   //If value is 1 then LED turns ON
      else if(data == '0')         //  Checks  whether value of data is equal to 0
         digitalWrite(13, LOW);    //If value is 0 then LED turns OFF
   }
}
```

### How Does it Works ??

HC 05/06 works on serial communication.here the android app is designed sending serial data to the bluetooth module when certain button is pressed.The Bluetooth module at other end receive the data and send to ardunio through the TX pin of bluetooth module(RX pin of arduino).The Code fed to arduino check the received data and compares.
If received data is 1 the LED turns on turns OFF when received data is 0

Open the serial monitor and watch the received data

![Serial1](https://igniteinnovateideas.files.wordpress.com/2016/04/serial1.png)

![Serial2](https://igniteinnovateideas.files.wordpress.com/2016/04/serial2.png)

### Android Application

In this tutorial I will not be covering tutorial on android app development.You can download the android application from here and the source code of the entire project

![android-logo](https://igniteinnovateideas.files.wordpress.com/2016/04/android-logo.png?w=150&h=150)

### How to use the app ?
Watch in video how to pair to bluetooth module

* Download the Application from here or here
* Pair your device with HC 05/06 bluetooth module

1) Turn ON HC 05/06 bluetooth module
2)Scan for available device
3)Pair to HC 05/06 by entering default password 1234 OR 0000

* Install  LED application on your android device
* Open the Application

![Splash](https://igniteinnovateideas.files.wordpress.com/2016/04/splash.png?w=262&h=449)

* Press paired devices
* Select your Bluetooth module from the List (hc 05/06)

![paired device](https://igniteinnovateideas.files.wordpress.com/2016/04/paired-device.png?w=255&h=437)

![avaiable device](https://igniteinnovateideas.files.wordpress.com/2016/04/avaiable-device.png?w=257&h=4400)

* After connecting successfully
* Press ON button to turn ON LED and OFF button to turn OFF LED

![LEDController](https://igniteinnovateideas.files.wordpress.com/2016/04/led.png?w=259&h=444)
![LEDAbout](https://igniteinnovateideas.files.wordpress.com/2016/04/about.png?w=260&h=446)
* Disconnect button to disconnect from bluetooth module
 

This is just basic tutorial on interfacing bluetooth module with arduino

This project can improved to higher level like **Home automation using smartphone, Smartphone controlled robot** and much more

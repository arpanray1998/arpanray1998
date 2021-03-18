Arpan Ray (25137), Aayush Hemdani(26321), Shardul Mishra

====== Flood Warning & Reservoir control system ======

{{:amc2020-2:110903472-cb139500-8307-11eb-80b8-385de099cd75.jpg?780|}}

Figure 1 showing Cheruthoni dam in Kerala, India (Source : https://fingfx.thomsonreuters.com/gfx/rngs/INDIA-FLOOD/010080MF18N/images/top.jpg)

=====Introduction=====

From highly critical infrastructure such as DAM's to agricultural reservoirs, artificial impoundments are subject to external environmental influences such as varying precipitation levels and floods. A reservoir system needs to adapt to the changing water levels to ensure that a certain water level is maintained to sustain its functionality. To do that, the inflow and outflow rates of water into and out of the system needs to be controlled and coordinated. One or more parts of such a system also has the potential to be used as a warning and alert system for major floods, that might damage such infrastructure. This project demonstrates a scaled down and simplified version of such a system. It uses the Arduino Uno as the core microcontroller coupled with other input and output devices that work inside a program loop tasked to continuously monitor water level in a reservoir and take suitable action if needed. This system is tasked with two main functions, 1) check water level if it crosses a predefined safe limit send off an alarm and start pumping. 2) If pumping capacity is exceeded switch to manual control and request human intervention to open the sluice gates and allow active drain until water level returns to safe level. The main components in this system is a Microcontroller, a Water pump, a servo emulating the sluice gate a buzzer for the alarm, an LCD display, an Ultrasonic sensor and a joystick controller for manual control. The Ultrasonic sensor module continuously sends and receives sound waves that reflect off the water surface and is received again providing the water level this data is then fed to the Microcontroller that takes the input and evaluates the level based on predefined safety levels and commands the output devices to operate in a manner such that the safety level of water can be maintained (Arpan Ray).

{{:amc2020-2:img_2987_2.jpg?600|}}

Figure 2 showing a representation of a typical Hydroelecrtric system and its components (Drawn, coloured and labelled by Shardul Mishra)

A Dam is an artificial obstruction to the flow of a river created intentionally to harness the kinetic energy stored in the flowing river stream as can be seen in figure 2. As a result, a reservoir is formed. This reservoir needs to maintain a certain level of water the volume of which the dam is able to withstand. If the volume increases, the Dam's structural integrity would be put to risk and after a threshold volume the dam wall will no longer be able to hold back the impoundment and collapse. This can cause damage to human lives and critical infrastructure such as Hydel power stations that can cause blackout in the region for months. To prevent such a scenario, a system for flood warning and control is essential that can detect the increase in the water level in the reservoir by monitoring it continuously and set off alarms depending on various levels of risk. Furthermore the dam gate may need to be opened if the pumping capacity is exceeded to save the structure from collapsing. This is done through manual human intervention as the system sets of a continuous alarm warning the Dam control crew members to open the gate to the required extent in order to drain the excess water to bring it down within the pumping capacity again after which it may again be closed.

The system prototype demonstrated in this project is a highly simplified version of the real system since a real reservoir would have many more parts and complicated connections but the flow of control shown in this demonstration will remain the same. This system may also be expanded to perform many more useful functions and tailored to specific needs such as remote monitoring, telemetry through MQTT, implementation to monitor natural impoundments such as Glacial Lakes, Rivers etc where cheap, simple, robust and easy to maintain systems are necessary which would require minimal maintenance in remote Mountain areas (Arpan Ray).

=====Materials & Methods=====

===Method===

The purpose of this project is to demonstrate a situation which shows how a dam and an impoundment will respond in the condition of the flood caused by heavy rainfall. Two situations are taken into account while assessing the contrasting flood conditions. In the first condition, the water level of the dam will rise due to intense rainfall. A temporary pump that has been installed will be sufficient to drain and the excess water will be drained out. The second situation is that due to continuous rainfall, the water level is still rising even though the pump is active, the overall reservoir water level is still rising because the pumping capacity is exceeded. The ultrasonic sensor is measuring the water level rise and gives an alert signal that the critical water limit has been crossed and the dam structural integrity is in danger. With the help of the manual control by joystick, the servo motor will open the gate. Now in this situation, the water outflow will have two directions; from the water pump as well as from the servo. This output flow rate is much higher than the input rainfall which will cause the water level comes down to its normal level and then the green led will go up (Ayush Hemdani). 

To achieve this an artificial symbolic Reservoir has been setup as can be seen in Figures 3 & 4 and has been graduated with a marker for ease of interpretation.

{{:amc2020-2:amc_reservoir.jpg?300|}}.   {{:amc2020-2:amc_setup.jpg?376|}}

Figures 3 & 4 showing the system setup (Photo : Arpan Ray)

===Circuit Schematic diagram===

{{:amc2020-2:amc.jpg?700|}}

Figure 5 Circuit schematic Diagram (Drawn by Arpan Ray using Fritzing)

===Materials Used===

1. Arduino Uno :

{{:amc2020-2:img_2718.jpg?200|}}

Figure 6 showing Arduino Uno Microcontroller board (Photo : Shardul Mishra)

It is a microcontroller board based on the ATmega328P (datasheet). It has 14 digital input/output pins (of which six can be used as PWM (Pulse Width Modulation) outputs), six analog inputs, a 16 MHz ceramic resonator (CSTCE16M0V53-R0), a USB connection, a power jack, an ICSP header and a reset button. Arduino Uno contains everything needed to support the microcontroller; simply connect it to a computer with a USB cable or power it with an AC-to-DC adapter or battery to get started. Arduino board itself is just a printed circuit board with the integrated circuit inside. Pin headers are also attached, which allows the integrated circuit to connect with the simulated software on the computer via USB cable. It helps the user perform logical computation by reading the inputs from a sensor or pushing a push-button and results in an output such as an alarm signal or start of a servo motor. For example, if the soil is dry, add some water; if the sun is shiny, keep the air conditioner (like a logic gate OR, AND, NAND, NOT, NOR, EXOR, e.t.c) (Aayush Hemdani). 

ATmega328P (datasheet) Link : http://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers ATmega328P_Datasheet.pdf

Arduino Uno Link: https://store.arduino.cc/arduino-uno-rev3

2. ultrasonic sensor :

{{:amc2020-2:img_2723.jpg?200|}}

Figure 7 showing an Ultrasonic sensor module (Shardul Mishra)

It transmits ultrasonic waves into the air and detects reflected waves from an object. There are many ultrasonic sensors applications, such as intrusion alarm systems, automatic door openers and backup sensors for automobiles. This ultrasonic sensor module HC - SR04 has a non-contact measurement function that operates between 2cm to 400cm. The module includes ultrasonic transmitters, receiver and control circuit. It consists of a four-pin wire connection which includes a 5Volt power supply, trigger pulse, echo pulse and ground. It works on a principle in which an IO trigger is used for at least 10us high-level signal. In response, the module automatically sends eight 40 kHz and detect whether there is a pulse signal back. If the signal is back, through high level, time of high output IO duration is the time from sending ultrasonic to returning. Test distance = (high level time×velocity of sound (340M/S) / 2. More details can be found in the source given below. (Aayush Hemdani)

Source:https://www.electroschematics.com/wp-content/uploads/2013/07/HCSR04-datasheet-version-1.pdf

3. Breadboard :

{{:amc2020-2:img_2725.jpg?200|}}

Figure 8 showing a Breadboard (Shardul Mishra)


It is a solderless device that is used to prototype electronic circuits. The standard large size and slightly smaller size are the most common ones which are used. Also, some of the breadboards come with binding posts for power sources as well. The working process of each one of them is almost the same, regardless of which ones are used for the circuit test run. Bigger breadboards have lines running all the way down the longer side which are known as the power lines, where the microcontroller or power supply can be plugged into them to supply power to the components. On the inside running perpendicular to these power lines are the lines or holes where the components are placed to build a circuit. These holes in the lines are connected by strips of metal underneath the board (Aayush Hemdani).

Source: http://wiring.org.co/learning/tutorials/breadboard/

4.(16 x 2) LCD :

{{:amc2020-2:img_2726.jpg?200|}}                                   {{:amc2020-2:screenshot_2021-03-18_at_8.29.16_am.png?200|}}

Figure 9 showing an LCD screen (Shardul Mishra)                    (Source : https://www.elprocus.com/lcd-16x2-pin-configuration-and-its-working/)



It is a general-purpose Liquid Crystal Display that consists of 16 columns and 2 rows. It consists of a total of 16 pins connections. Pin 1 is used to connect the GND terminal of the microcontroller unit or power source. Pin 2 is used to connect the supply pin of the power source. The variable resistor can be connected to Pin 3 to vary the display contrast. Pin 4 toggles among command or data register whereas Pin 5 is used to read or write the data. Pin 6 is an Enable/Control Pin which should be held high to execute the Read/Write process. Pins 7-14 are Data Pins that are used to send data to the display. These pins are connected in two-wire modes like 4-wire mode and 8-wire mode. In 4-wire mode, only four pins are connected to the microcontroller unit like 0 to 3, whereas in 8-wire mode, 8-pins are connected to the microcontroller unit like 0 to 7. Pin15 (+ve pin of the LED) is connected to +5V which is the working potential. and Pin 16 (-ve pin of the LED) is connected to GND (Aayush Hemdani).

Source: https://components101.com/16x2-lcd-pinout-datasheet

Youtube Source: https://youtu.be/dZZynJLmTn8

5. Water pump :

{{:amc2020-2:img_2729.jpg?200|}}

Figure 10 showing a Water pump (Shardul Mishra)


This is a submersible mini water pump that is operated at a voltage and current rating of 3-5 volt and 100-200 mA respectively. It provides a large flowrate of 100 Liters/Hour. More product description can be found in the source provided below (Aayush Hemdani).

Source: https://www.amazon.de/-/en/RUNCCI-YUN-Submersible-Aquarium-Watering-Vertical/dp/B08BZBN29C/ref=sr_1_8?crid=NIO0JYX67CVX&dchild=1&keywords=wasserpumpe+5v&qid=1610404102&sprefix=water+pump+%2Caps%2C202&sr=8-8

6. Single Channel Relay :

{{:amc2020-2:img_2721.jpg?200|}}

Figure 11 showing a Single channel Relay switch (Shardul Mishra)


A Single channel Relay is an electromechanical Relay module device that uses an electric current to open or close the contacts of a switch. It consists of input pins (Relay trigger, Ground, Vcc) and output sources (Normally open (NO), Normally Closed (NC) and common). The small transistor on the relay magnetizes the magnetic coil inside when the input current is applied. This enables the contacts (NO, NC) connection and as result LED indicates the working status of the relay. The operating voltage is between (5-12) Volts and for each channel, the input signal is 3-5 Volts. The maximum AC load current is 10 Amps at 250/125 DC and the Maximum DC load current is 10 Amps at 30/28 DC (Aayush Hemdani). 

Source: https://components101.com/switches/5v-relay-pinout-working-datasheet

7. Arduino Power Module :

{{:amc2020-2:img_2722.jpg?200|}}

Figure 12 showing a Arduino power module (Shardul Mishra)


The power module used is a 3.3 Volts and 5Volts Breadboard Power Supply Module with series diode, polarity reversal protection. The module can take between (6.5-12) Volts of input supply and can give output between (3.3-5) Volts. The External input voltage can be provided by this power module by an ON/OFF switch. This Module provides the external power to the water pump especially in the second situation when the water level keeps on rising because of the continuous rainfall (Aayush Hemdani). 

Source: http://www.handsontec.com/dataspecs/mb102-ps.pdf

8. I2C Interface :

{{:amc2020-2:05bf3236-5a7e-4787-98d4-c93654deb185.jpg?200|}}

Figure 13 showing a I2C interface (Shardul Mishra)


It is an interface that provides communication between a master and multiple slave devices or even multiple master devices. Here in this project, this interface is used to communicate between the LCD display with two lines SCL(Serial Clock) and SDA(Serial Data). The SCL line is the clock signal that synchronises the data transfer between the devices on the I2C bus and the SDA line carries the data (Aayush Hemdani).

Source: https://howtomechatronics.com/tutorials/arduino/how-i2c-communication-works-and-how-to-use-it-with-arduino/
 


9. AC/DC Adapter :

{{:amc2020-2:img_2708.jpg?200|}}

Figure 14 showing an AC/DC adapter (Shardul Mishra)



An AC/DC adapter is made up of a central unit that draws power from an AC outlet, it then converts the power to DC that is used to charge the device. Each AC adapter has a specific power rating, measured in volts or watts that it can handle and the output of a device (Aayush Hemdani).

10. LED :

{{:amc2020-2:img_2731.jpg?200|}}

Figure 15 showing LED lights (Shardul Mishra)


It is a PN  junction diode that emits light when it is activated. The PN junction is surrounded by a transparent hard plastic epoxy reason hemispherical shaped shell to protect the diode from external shock. When a sufficient voltage is applied then the electrons are capable of recombining with the electron holes within the device which releases the energy in the form of photons. This effect is called electroluminescence, and the colour of the light is determined by the energy bandgap of the semiconductor. LEDs are made from direct gap semicondu++-ctor compounded such as Gallium Arsenide, Gallium Phosphide, Gallium Arsenide Phosphide, Silicon Carbide and Gallium Indium nitride. Also, they may be mixed together at different ratios to produce more distinct wavelengths of colours (Aayush Hemdani).

Source: https://www.toppr.com/bytes/principles-of-led/#:~:text=Working%20Principle%3A,in%20the%20form%20of%20photons.

11. Piezoelectric buzzer :

{{:amc2020-2:img_2719.jpg?200|}}

Figure 16 showing Piezoelectric buzzer (Shardul Mishra)


A buzzer is a very small and compact 2-pin component that creates the beep sound due to the internal oscillating circuit present inside it. pin-1 is a long terminal lead(+) that can be powered by 6 Volt DC and pin-2 is a short terminal lead(-) that is connected to the Ground. The operating Voltage is 4-8 Volt DC and the rated current is less than 30 mA. The Resonant Frequency approximately 2300 Hz. Also, the buzzer is normally connected with a switching circuit to turn ON or OFF the buzzer at the required time and require interval (Aayush Hemdani).

Source: https://components101.com/misc/buzzer-pinout-working-datasheet

12. Servo motor :

{{:amc2020-2:img_2720.jpg?200|}}

Figure 17 showing Servo motor (Shardul Mishra)


Servo motor has integrated gears and a shaft that can be precisely controlled by varying the angles of the positioned shaft between 0 and 180 degrees which eventually results in a set of various speeds. Servo motors have three wires which are red, black and brown power, ground, and signal. The power wire is typically red and should be connected to the 5 Volts pin on the Arduino board. The ground wire is typically black or brown and should be connected to a ground pin on the Arduino board (Aayush Hemdani).

13. Jumper wires :

{{:amc2020-2:img_2728.jpg?200|}}

Figure 18 showing Jumper wires (Shardul Mishra)

 
Jumper wires are frequently used to avoid the hassle of soldering as they used for making connections between two points to each other on a breadboard. These wires help to experiment if in case there are any last-minute working changes within the circuit (Aayush Hemdani).

14. Joystick Controller :

{{:amc2020-2:img_2724.jpg?200|}}

Figure 19 showing Joystick controller (Shardul Mishra)

The joystick switch has been used to demonstrate manual control of rising water level in case of uncontrolled rainfall. Joystick module consists of 5 pin, which includes Ground, Vcc, VRx, VRy and switch. It has an internal potentiometer value of 10k and 5-volt operating voltage. It has two independent potentiometers, one for each axis (x and y) and both potentiometers are independent to move in their particular direction. The switch helps to connect the joystick Module with Arduino and get an analogue output based on the direction of movement of the Joystick Knob. More product description can be found in the source provided below (Aayush Hemdani).

Source: https://components101.com/modules/joystick-module

Amazon source: https://www.amazon.de/-/en/PS2-Game-Joystick-Biaxialen-Control-Raspberry/dp/B06Y1HB7KR/ref=sr_1_17?dchild=1&keywords=arduino+joystick+schalter&qid=1616047952&sr=8-17

=====Code Block programmed in Arduino IDE=====

Code written by Arpan Ray

<file c++ AMC.ino>

/* This Code belongs to the AMC project Flood Warning and DAM Control */

#include <Wire.h>                             // including Wire Library for I2C
#include <Servo.h>                            // including servo library for servo control
#include <LiquidCrystal_I2C.h>                // including NewLiquidCrystal Library for LCD with I2C
LiquidCrystal_I2C lcd(0x27, 16, 2);           // I2C address 0x27, 16 column and 2 rows

Servo myservo;                                // creating a servo object to control a servo

// defining variables :

#define echoPin 2                             // attach pin D2 Arduino to pin Echo of HC-SR04
#define trigPin 3                             //attach pin D3 Arduino to pin Trig of HC-SR04
#define JOY_X A0
#define JOY_Y A1
#define VCC_JOY_Pin A2
#define GND_JOY_Pin A3

// initialising variables :

int X_Value = 0;                              // initialising joystick X axis value to be 0
int Y_Value = 0;                              // initialising joystick Y axis value to be 0
int led_RED = 5;                              // initializing the pin for Red LED as digital pin 5
int led_GREEN = 4;                            // initializing the pin for Green LED as digital pin 4
long duration;                                // variable for the duration of sound wave travel
const int JOY_SW = 8;                         // variable to store the servo position as per commands from the joystick
int distance;                                 // variable for the distance measurement
int pump_relay =6;                            // initializing the signal pin of the relay module as digital pin 6.
const int buzzer = 12;                        // initialising the buzzer in the pin 12 of arduino UNO

void setup()
{
  Serial.begin(9600);
  pinMode(JOY_SW, INPUT);                     // Setting the pinmodes to 'OUTPUT' or 'INPUT' depending on component and function type
  digitalWrite(JOY_SW, HIGH);
  pinMode(VCC_JOY_Pin, OUTPUT);
  pinMode(GND_JOY_Pin, OUTPUT);
  pinMode (led_RED, OUTPUT);
  pinMode (led_GREEN, OUTPUT); 
  digitalWrite(VCC_JOY_Pin, HIGH);
  digitalWrite(GND_JOY_Pin, LOW);
  myservo.attach(9);                          // attaches the servo on pin 9 to the servo object created above
  lcd.begin();
  lcd.backlight();
  lcd.print("GLOF Monitoring");
  lcd.setCursor(0,1);                         // setting the cursor of the LCD screen at the start of the second row.
  lcd.print("     System    ");
  delay(3000);
  lcd.clear();
  lcd.setCursor (0,0);                        // setting the cursor of the LCD screen at 0,0.
  lcd.print ("Monitoring Lake ");             // printing "status:" on the first row
  lcd.setCursor(0,1);                         // setting the cursor of the LCD screen at the start of the second row.
  lcd.print("  Water Level..   ");
  delay(4000);
  lcd.clear();
  lcd.setCursor (0,0);                        // setting the cursor of the LCD screen at 0,0.
  lcd.print ("Water Level");                  // printing "status:" on the first row
  lcd.setCursor(0,1);                         // setting the cursor of the LCD screen at the start of the second row.
  lcd.print("       - SAFE ");
  pinMode (pump_relay, OUTPUT);
  pinMode(trigPin, OUTPUT);                   // Sets the trigPin as an OUTPUT
  pinMode(echoPin, INPUT);                    // Sets the echoPin as an INPUT
  pinMode(buzzer, OUTPUT);                    // Sets Buzzer pin 12 as OUTPUT
  Serial.begin(9600);                         // Serial Communication is starting with 9600 of baudrate speed
}

void loop() 
{
  X_Value = analogRead(JOY_X);
  Y_Value = analogRead(JOY_Y);
  Serial.print(X_Value);
  Serial.print("\t");
  Serial.println(Y_Value);
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);          // Reads the echoPin, returns the sound wave travel time in microseconds
  distance = duration * 0.034 / 2;            // Speed of sound wave divided by 2 (go and back)
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if (distance <= 12 && distance >=10)
  {
    digitalWrite (led_RED, HIGH);
    digitalWrite (led_GREEN, LOW);
    tone(buzzer, 1000);                       // Send 1KHz sound signal...
    delay(1000);                              // ...for 1 sec
    noTone(buzzer);                           // Stop sound...
    delay(1000);                              // ...for 1sec
    lcd.clear();                              // clearing memory.
    lcd.setCursor (0,0);                      // setting the cursor of the LCD screen at 0,0.
    lcd.print ("  !!DANGER!!  ");             // printing "status:" on the first row
    lcd.setCursor(0,1);                       // setting the cursor of the LCD screen at the start of the second row.
    lcd.print("  Flood Risk");
    delay(2000);
    lcd.clear();                              // clearing memory.
    lcd.setCursor (0,0);                      // setting the cursor of the LCD screen at 0,0.
    lcd.print ("   Water Pump");              // printing "status:" on the first row
    lcd.setCursor(0,1);                       // setting the cursor of the LCD screen at the start of the second row.
    lcd.print("     Active   ");
    delay(1000);
    digitalWrite (pump_relay, HIGH);          //turning the relay pin on which in turn switches on the water pump.
    delay(1000);
   }
   else if (distance <= 9 && distance >= 7)
  {
    digitalWrite (led_RED, HIGH);
    digitalWrite (led_GREEN, LOW);
    tone(buzzer, 100);                        // Send 1KHz sound signal...
    delay(1000);                              // ...for 1 sec
    tone(buzzer, 1000);
    delay(1000);
    tone(buzzer, 100);
    delay(1000);
    tone(buzzer, 1000);
    delay(1000);
    tone(buzzer, 100);
    delay(1000);
    noTone(buzzer);                           // Stop sound...
    delay(100);                               // ...for 1sec
    digitalWrite (pump_relay, HIGH);
    lcd.clear();                              // clearing memory.
    lcd.setCursor (0,0);                      // setting the cursor of the LCD screen at 0,0.
    lcd.print ("Pumping Capacity");           // printing "status:" on the first row
    lcd.setCursor(0,1);                       // setting the cursor of the LCD screen at the start of the second row.
    lcd.print("    Exceeded   ");
    delay(2000);
    lcd.clear();                              // clearing memory.
    lcd.setCursor (0,0);                      // setting the cursor of the LCD screen at 0,0.
    lcd.print ("Switching to");               // printing "status:" on the first row
    lcd.setCursor(0,1);                       // setting the cursor of the LCD screen at the start of the second row.
    lcd.print("Manual Control...   ");
    delay(2000);
    lcd.clear();                              // clearing memory.
    lcd.setCursor (0,0);                      // setting the cursor of the LCD screen at 0,0.
    lcd.print ("   OPEN DAM");                // printing "status:" on the first row
    lcd.setCursor(0,1);                       // setting the cursor of the LCD screen at the start of the second row.
    lcd.print(" CONTROL GATES");
    delay(1000);
        while (analogRead(JOY_Y) > 514)
        {
          int JOY_Pin = analogRead(JOY_Y);
          digitalWrite (led_RED, HIGH);
          digitalWrite (led_GREEN, LOW);      // turning the Green LED light on.
          myservo.write((JOY_X - 520)/10);
          tone(buzzer, 152);
          lcd.clear();                        // clearing memory.
          lcd.setCursor (0,0);                // setting the cursor of the LCD screen at 0,0.
          lcd.print ("EMERGENCY WATER");      // printing "status:" on the first row
          lcd.setCursor(0,1);                 // setting the cursor of the LCD screen at the start of the second row.
          lcd.print("RELEASE ACTIVE");
        }
    }
   else if(distance > 12)
  {
    noTone(buzzer);                           // Stop sound...
    delay(100);
    myservo.write((JOY_X + 520)/10);
    lcd.clear();                              // clearing memory.
    lcd.setCursor (0,0);                      // setting the cursor of the LCD screen at 0,0.
    lcd.print ("Water Level:");               // printing "status:" on the first row
    lcd.setCursor(0,1);                       // setting the cursor of the LCD screen at the start of the second row.
    lcd.print("        - SAFE   ");
    digitalWrite (led_GREEN, HIGH);           // turning the Green LED light on.
    digitalWrite (led_RED, LOW);
    digitalWrite (pump_relay, LOW);
    delay(1000);
  }
}
  
</file>



=====Results=====

Video below demonstrates the working of the prototype that aims to show the Flow of Control - Arpan Ray, Shardul Mishra, Ayush Hemdani

{{ :amc2020-2:amc_video.mp4?700 |}}

=====Discussion & Conclusion=====

The system worked as expected although certain things needed to be adjusted. The main challenge faced was that the system was getting overloaded when we tried to demonstrate situation 2 i.e in situation 2, as the water level was slowly rising, we would expect that first the alarm for situation 1 would go off and the water pump would start after which the situation 2 alarm would go off. This unfortunately did not happen. The system responded directly to situation 2 although the code shows that the control sequence places sit. 1 before sit. 2. We think that this maybe due to an overloaded system where too many input and output operations are taking place simultaneously. Another problem was that the connector pins were coming out of the male - female connectors because of loose connections and this problem was resolved by taping the two ends of the wires. 

Overall by implementing this project we got to learn a great deal about such control systems and its related electronics. This has given us the impetus to think bigger and explore new ideas. This is a simple demonstration of the flow of control to prevent overloading and collapse of a reservoir but can be expanded by the inclusion of real-time data transfer and remote monitoring can be done using MQTT and Node-red which would allow us to transfer store and analyse data remotely away from harsh environments. (Shardul Mishra, Arpan Ray, Aayush Hemdani)

=====References=====

  * http://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers ATmega328P_Datasheet.pdf (Date accessed: 20th January 2021)
  * https://www.electroschematics.com/wp-content/uploads/2013/07/HCSR04-datasheet-version-1.pdf (Date accessed: 20th January 2021)
  * http://wiring.org.co/learning/tutorials/breadboard/ (Date accessed: 20th January 2021)
  * https://www.elprocus.com/lcd-16x2-pin-configuration-and-its-working/ (Date accessed: 20th January 2021)
  * https://components101.com/16x2-lcd-pinout-datasheet (Date accessed: 20th January 2021)
  * https://www.amazon.de/-/en/RUNCCI-YUN-Submersible-Aquarium-Watering-Vertical/dp/B08BZBN29C/ref=sr_1_8?crid=NIO0JYX67CVX&dchild=1&keywords=wasserpumpe+5v&qid=1610404102&sprefix=water+pump+%2Caps%2C202&sr=8-8(Date accessed: 26th January 2021)
  * https://components101.com/switches/5v-relay-pinout-working-datasheet (Date accessed: 26th January 2021)
  * http://www.handsontec.com/dataspecs/mb102-ps.pdf (Date accessed: 26th January 2021)
  * https://howtomechatronics.com/tutorials/arduino/how-i2c-communication-works-and-how-to-use-it-with-arduino/ (Date accessed: 26th January 2021)
  * https://www.toppr.com/bytes/principles-of-led/#:~:text=Working%20Principle%3A,in%20the%20form%20of%20photons (Date accessed: 26th January 2021)
  * https://components101.com/misc/buzzer-pinout-working-datasheet (Date accessed: 26th January 2021)
  * https://components101.com/modules/joystick-module (Date accessed: 26th January 2021)

======Group Members======


1) Arpan Ray - (25137)

2) Aayush Hemdani - (26321)

3) Shardul Mishra - (27241)

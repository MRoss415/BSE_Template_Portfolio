# Sun Tracking Solar Panel
The goal of this project is to make a sustainable generator and power bank that can be used to power anything via an outlet attatchment. After the solar panel system is in place, I plan to implement a 3-prong sustainable energy system, combining solar, wind, and hydroelectric power options to make it as effective and sustainable as possible.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Michael R | Marin Academy | Physics, Mechanical/Electrical Engineering | Incoming Senior

![headstone image](https://user-images.githubusercontent.com/88206259/129399652-92707d40-e4cf-4876-958f-25e6340f13fe.jpg)

  
# Final Milestone
My final milestone is mounting my sun tracking solar panel onto a buoyant chassis alongside hydroelectric generators I integrated into the hull and wind turbines. I hope to increase the efficiency of the ship so as it is already propelled through the water by its base power source and motor, it is constantly generating electricity and either recharging the base power source or an additional one. This allows it to increase its possible distance, and can even allow it to forgo refueling if it wanted by simply waiting to recharge in the water. Additionally, if the ship was ever stranded, it would have the ability to sit idly in the water and fully recharge itself.

[![Final Milestone]()](https://www.youtube.com/watch?v=3npqKn-eHq0){:target="_blank" rel="noopener"}

# Presentation
<iframe width="560" height="315" src="https://www.youtube.com/embed/KJTtlT2HPKg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Second Milestone
My second milestone was the completion of my solar panel circuit. The circuit consisted of a lithium battery that I connected to a power booster to boost the voltage of the solar panel from 3.3V to 5V, soldering a capacitor to the power booster that regulates the voltage between the three, and finally connecting the three to a USB/DC solar connector. On this connector, I soldered on the USB input and the connection from the power booster, before completing the circuit by striping down the connectors on the solar panel and attatching them to a DC input so it can connect to the power booster. 

# CAD Designs
![SPassemblycadpictures](https://user-images.githubusercontent.com/88206259/130507157-b4359650-5e02-4cf8-aaaf-4c0742b19f78.jpg)

# First Milestone  
My first milestone was establishing the sun traking system for the solar panel. I began by posisitioning two photoresistors on opposite ends of a breadboard connected to an Arduino, and connecting a servo to that. I then wrote up some code in C++ that monitors the output values from both photoresistors so that if one rises above the other, the servo will activate until both values are equal again. This will result with the solar panel continuously tracking the sun.

<iframe width="560" height="315" src="https://www.youtube.com/embed/3npqKn-eHq0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Circuit Diagram
![SunTrackerCircuitDiagram](https://user-images.githubusercontent.com/88206259/127694933-1066e222-f0d3-40d6-a2e3-3bad213a5b66.jpg)

# Sun Tracking Code
```arduino
#include <Servo.h>
Servo myservo;

const int pResistor1 = A0;
const int pResistor2 = A1;

int deg;
int value1;
int value2;

void setup() {
  // put your setup code here, to run once:
  myservo.attach(9);
  myservo.write(90);
  deg = 90;
  myservo.write(deg);
  pinMode(pResistor1, INPUT);
  pinMode(pResistor2, INPUT);
  Serial.begin(9600);
} 

void loop() {
  // put your main code here, to run repeatedly:
  value1 = analogRead(pResistor1);
  value2 = analogRead(pResistor2);
    Serial.print("pResistor1 ");
    Serial.println(value1);
    Serial.print("pResistor2 ");
    Serial.println(value2);

  if (value1 > value2 && deg < 180) {
    deg = deg + 15;
    myservo.write(deg);
  }
  if (value1 < value2 && deg > 0) {
    deg = deg - 15;
    myservo.write(deg);
  }
  delay(500);
  Serial.print("Deg");
  Serial.println(deg);
}
```

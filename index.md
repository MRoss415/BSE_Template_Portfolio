# Sun Tracking Solar Panel
The goal of this project is to make a sustainable generator and power bank that can be used to power anything via an outlet attatchment. After the solar panel system is in place, I plan to implement a 3-prong sustainable energy system, combining solar, wind, and hydroelectric power options to make it as effective and sustainable as possible.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Michael R | Marin Academy | Physics, Mechanical/Electrical Engineering | Incoming Senior

![Headstone Image](https://bluestampengineering.com/wp-content/uploads/2016/05/improve.jpg)
  
# Final Milestone
Example: My final milestone is the increased reliability and accuracy of my robot. I ameliorated the sagging and fixed the reliability of the finger. As discussed in my second milestone, the arm sags because of weight. I put in a block of wood at the base to hold up the upper arm; this has reverberating positive effects throughout the arm. I also realized that the forearm was getting disconnected from the elbow servo’s horn because of the weight stress on the joint. Now, I make sure to constantly tighten the screws at that joint. 

[![Final Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612573869/video_to_markdown/images/youtube--F7M7imOVGug-c05b58ac6eb4c4700831b2b3070cd403.jpg )](https://www.youtube.com/watch?v=3npqKn-eHq0){:target="_blank" rel="noopener"}

# Second Milestone
My second milestone was the completion of my solar panel circuit. The circuit consisted of a lithium battery that I connected to a power booster to boost the voltage of the solar panel from 3.3V to 5V, soldering a capacitor to the power booster that regulates the voltage between the three, and finally connecting the three to a USB/DC solar connector. On this connector, I soldered on the USB input and the connection from the power booster, before completing the circuit by striping down the connectors on the solar panel and attatching them to a DC input so it can connect to the power booster. 

[![Second Milestone](<iframe width="560" height="315" src="https://www.youtube.com/embed/FfrBfv0-a6A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>] (https://www.youtube.com/embed/FfrBfv0-a6A){:target="_blank" rel="noopener"}
# First Milestone
  
My first milestone was establishing the sun traking system for the solar panel. I began by posisitioning two photoresistors on opposite ends of a breadboard connected to an Arduino, and connecting a servo to that. I then wrote up some code in C++ that monitors the output values from both photoresistors so that if one rises above the other, the servo will activate until both values are equal again. This will result with the solar panel continuously tracking the sun.

[![First Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612574117/video_to_markdown/images/youtube--CaCazFBhYKs-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=3npqKn-eHq0 "First Milestone"){:target="_blank" rel="noopener"}

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

  deg = 0;
  if (value1 > value2 && deg <= 180) {
    deg = deg + 1;
    myservo.write(deg);
  }
  if (value1 < value2 && deg >= 0) {
    deg = deg - 1;
    myservo.write(deg);
  }
  delay(500);
}
```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <div class="container">
        <h1>Underground Cable Fault Detection System using Arduino</h1>
        <h2>Introduction</h2>
        <p>This project demonstrates an underground cable fault detection system using Arduino. The system detects faults in underground cables and indicates the fault location to the user via an LCD display.</p>
        <h2>Components Required</h2>
        <ul>
            <li>Arduino Uno</li>
            <li>LCD Display (16x2)</li>
            <li>Relays</li>
            <li>Resistors</li>
            <li>LEDs</li>
            <li>Diodes (1N4007)</li>
            <li>Buzzer</li>
            <li>Switches</li>
            <li>ULN2003A</li>
        </ul>
        <h2>Circuit Diagram</h2>
        <div class="image-container">
            <img src="https://github.com/HARISHWINNER/Underground_Cable_Fault_Detection/blob/f2c1a898e433a157306e57154a5e9158468c420b/How%20to%20make%20a%20Underground%20Cable%20Fault%20Detection%20using%20Arduino.png" alt="Underground Cable Fault Detection Circuit Diagram">
        </div>
        <h2>Working Principle</h2>
        <p>The system works by sending a signal through the cable and measuring the return signal. If a fault is detected, the location of the fault is displayed on the LCD screen. The fault is indicated by turning on the corresponding LED and sounding a buzzer.</p>
        <h2>Code</h2>
        <p>Below is the Arduino code used in this project:</p>
        <pre><code>
#include &lt;LiquidCrystal.h&gt;

LiquidCrystal lcd(2, 3, 4, 5, 6, 7);

int led1 = 10;  // for Red led
int led2 = 11;  // for Yellow led
int led3 = 12;  // for Green led

void setup() {
  lcd.begin(16, 2);
  lcd.print("CABLE FAULT");
  lcd.setCursor(0, 1);
  lcd.print("DETECTION");
  delay(2000);
  lcd.clear();
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
}

void loop() {
  int faultType = checkFault();  // function to check fault type

  lcd.setCursor(0, 0);
  if (faultType == 1) {
    lcd.print("Fault at RED");
    digitalWrite(led1, HIGH);
    digitalWrite(led2, LOW);
    digitalWrite(led3, LOW);
  } else if (faultType == 2) {
    lcd.print("Fault at YELLOW");
    digitalWrite(led1, LOW);
    digitalWrite(led2, HIGH);
    digitalWrite(led3, LOW);
  } else if (faultType == 3) {
    lcd.print("Fault at GREEN");
    digitalWrite(led1, LOW);
    digitalWrite(led2, LOW);
    digitalWrite(led3, HIGH);
  } else {
    lcd.print("No Fault");
    digitalWrite(led1, LOW);
    digitalWrite(led2, LOW);
    digitalWrite(led3, LOW);
  }
  delay(1000);
}

int checkFault() {
  // Your fault detection logic here
  // Return 1 for Red fault, 2 for Yellow fault, 3 for Green fault, 0 for no fault
  return random(0, 4);  // random fault generator for testing
}
        </code></pre>
        <h2>How to Run</h2>
        <ol>
            <li>Connect the components as shown in the circuit diagram.</li>
            <li>Upload the Arduino code to your Arduino Uno.</li>
            <li>Power on the system.</li>
            <li>Observe the LCD display for fault locations.</li>
        </ol>
        <h2>Clone the Repository</h2>
        <p>To clone this repository, use the following command:</p>
        <pre><code>git clone https://github.com/HARISHWINNER/underground-cable-fault-detection.git</code></pre>
        <h2>Conclusion</h2>
        <p>This underground cable fault detection system is a simple and effective way to monitor and locate faults in underground cables. It can be further enhanced with more advanced fault detection algorithms and components.</p>
        <h2>License</h2>
        <p>This project is licensed under the MIT License.</p>
    </div>
</body>
</html>

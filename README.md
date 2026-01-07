# 🔘 Toggle an LED Using a Button (Arduino – Wokwi Simulation)

## 📌 Project Overview
This project demonstrates how to **toggle an LED ON and OFF using a push button** with an **Arduino Uno**.  
Each button press changes the LED state using simple **digital input/output logic**.  
The circuit and code are simulated using **Wokwi**, an online Arduino simulator.

---

## 🎯 Objective
- To understand **digital input and output** in Arduino
- To learn how to use a **push button with INPUT_PULLUP**
- To implement **LED toggle logic**
- To practice **Arduino simulation using Wokwi**

---

## 🛠️ Components Used
- Arduino Uno  
- LED  
- Push Button  
- 220Ω Resistor  
- Jumper Wires  

---

## 🔌 Circuit Connections

### LED
- LED Anode (long leg) → **Pin 13**
- LED Cathode (short leg) → **220Ω Resistor**
- Resistor → **GND**

### Push Button
- One terminal → **Pin 2**
- Other terminal → **GND**

> Note: Internal pull-up resistor is enabled in code, so no external resistor is required for the button.

---

## 💻 Arduino Code

```cpp
int ledPin = 13;
int buttonPin = 2;

int ledState = LOW;
int lastButtonState = HIGH;

void setup() {
  pinMode(ledPin, OUTPUT);
  pinMode(buttonPin, INPUT_PULLUP);
}

void loop() {
  int buttonState = digitalRead(buttonPin);

  if (buttonState == LOW && lastButtonState == HIGH) {
    ledState = !ledState;          // Toggle LED state
    digitalWrite(ledPin, ledState);
    delay(200);                    // Debounce delay
  }

  lastButtonState = buttonState;
}

# Control-a-28BYJ-48-Stepper-Motor-with-RGB-LED-on-Arduino-5-Color-Motor-Project-Tutorial-
# Control a 28BYJ-48 Stepper Motor with RGB LED on Arduino

## Overview
This project demonstrates how to control a 28BYJ-48 stepper motor with an RGB LED on Arduino. The motor movements (full rotation, quarter rotation, and pause) are associated with specific colors displayed on the RGB LED.

---

## Components
| **Component**             | **Quantity** | **Description**                                           |
|----------------------------|--------------|-----------------------------------------------------------|
| Arduino Uno               | 1            | Microcontroller to control the project                   |
| 28BYJ-48 Stepper Motor    | 1            | 4-phase stepper motor                                     |
| ULN2003 Driver Board      | 1            | Driver board for the 28BYJ-48 motor                      |
| RGB LED                   | 1            | Common cathode or common anode                           |
| Resistors (220Ω)          | 3            | For current limiting for RGB LED pins                   |
| Jumper Wires              | Several      | For making connections                                   |

---

## Connections
| **Component**             | **Pin**            | **Arduino Pin**           |
|----------------------------|--------------------|----------------------------|
| **ULN2003 Driver Board**   | IN1                | Pin 8                     |
|                            | IN2                | Pin 9                     |
|                            | IN3                | Pin 10                    |
|                            | IN4                | Pin 11                    |
|                            | GND                | GND                       |
|                            | 5V Power           | 5V                        |
| **RGB LED**                | Red pin            | Pin 5                     |
|                            | Green pin          | Pin 6                     |
|                            | Blue pin           | Pin 7                     |
|                            | Common Cathode     | GND                       |
|                            | (Common Anode)     | 5V                        |

---

## Functionality
1. **Stepper Motor Actions**:
   - Full clockwise rotation: RGB LED shows **Red**.
   - Quarter clockwise rotation: RGB LED shows **Green**.
   - Full counterclockwise rotation: RGB LED shows **Blue**.
   - Quarter counterclockwise rotation: RGB LED shows **Yellow**.
   - Pause state: RGB LED shows **Purple**.

2. **RGB LED Color Representation**:
   - Each motor action is visually represented by a unique color on the RGB LED.

---

## Arduino Code

Here’s the Arduino code for the project:

```cpp
#include <Stepper.h>

#define STEPS_PER_REV 2048 // Number of steps per revolution for the 28BYJ-48

// Define RGB LED pins
#define RED_PIN 5
#define GREEN_PIN 6
#define BLUE_PIN 7

// Define stepper motor pins
Stepper stepper(STEPS_PER_REV, 8, 10, 9, 11);

void setup() {
  // Initialize RGB LED pins as outputs
  pinMode(RED_PIN, OUTPUT);
  pinMode(GREEN_PIN, OUTPUT);
  pinMode(BLUE_PIN, OUTPUT);

  // Set stepper motor speed
  stepper.setSpeed(10); // 10 RPM
}

void loop() {
  // Full clockwise rotation
  setRGBColor(255, 0, 0); // Red
  stepper.step(STEPS_PER_REV); // Full rotation
  delay(1000);

  // Quarter clockwise rotation
  setRGBColor(0, 255, 0); // Green
  stepper.step(STEPS_PER_REV / 4); // Quarter rotation
  delay(1000);

  // Full counterclockwise rotation
  setRGBColor(0, 0, 255); // Blue
  stepper.step(-STEPS_PER_REV); // Full reverse rotation
  delay(1000);

  // Quarter counterclockwise rotation
  setRGBColor(255, 255, 0); // Yellow
  stepper.step(-STEPS_PER_REV / 4); // Quarter reverse rotation
  delay(1000);

  // Pause state
  setRGBColor(128, 0, 128); // Purple
  delay(2000);
}

// Function to set RGB LED color
void setRGBColor(int red, int green, int blue) {
  analogWrite(RED_PIN, red);
  analogWrite(GREEN_PIN, green);
  analogWrite(BLUE_PIN, blue);
}

To control a 28BYJ-48 stepper motor with an RGB LED on an Arduino, we can use the ULN2003 driver board to drive the motor and connect the RGB LED directly to the Arduino pins. This project includes five different colors to represent various stages of motor movement, providing both visual and functional feedback.
Components Needed
Arduino (e.g., Uno, Nano)
28BYJ-48 Stepper Motor with ULN2003 Driver Board
RGB LED (either common cathode or anode)
220Ω resistors (3, for each color pin of the RGB LED)
Jumper wires
Wiring Instructions
28BYJ-48 Stepper Motor and ULN2003 Driver
IN1 on the ULN2003 to Pin 8 on Arduino
IN2 on the ULN2003 to Pin 9 on Arduino
IN3 on the ULN2003 to Pin 10 on Arduino
IN4 on the ULN2003 to Pin 11 on Arduino
GND on ULN2003 to GND on Arduino
5V Power on ULN2003 to 5V on Arduino
RGB LED Connections
Red pin of RGB LED to Pin 5 on Arduino (use a 220Ω resistor in series)
Green pin of RGB LED to Pin 6 on Arduino (use a 220Ω resistor in series)
Blue pin of RGB LED to Pin 7 on Arduino (use a 220Ω resistor in series)
Common pin of RGB LED to GND on Arduino (if common cathode)
For a common anode LED, connect the common pin to 5V instead.
Explanation of the Code Functionality
The code below controls the motor’s movement and RGB LED color based on different rotations:

Full clockwise rotation — RGB LED is Red.
Quarter clockwise rotation — RGB LED is Green.
Full counterclockwise rotation — RGB LED is Blue.
Quarter counterclockwise rotation — RGB LED is Yellow.
Pause state — RGB LED is Purple.
Code Explanation
Stepper Motor Setup: The Stepper library initializes the motor with the specified number of steps and connected pins.
RGB Color Function: The setRGBColor() function uses analogWrite() to control the brightness of each LED color pin, creating various colors.
Loop Structure: Each movement of the motor has an associated color:
Full clockwise rotation with Red (255, 0, 0).
Quarter clockwise rotation with Green (0, 255, 0).
Full counterclockwise rotation with Blue (0, 0, 255).
Quarter counterclockwise rotation with Yellow (255, 255, 0).
Paused state with Purple (128, 0, 128).
Summary
This code allows the 28BYJ-48 stepper motor to perform rotations with color feedback on an RGB LED. Each action in the motor’s sequence corresponds to a specific color, providing an interactive and visually engaging way to track the motor’s state and direction. Adjust motor speed, step count, and delay times as needed to achieve different behaviors.

# Control-a-28BYJ-48-Stepper-Motor-with-RGB-LED-on-Arduino-5-Color-Motor-Project-Tutorial-
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

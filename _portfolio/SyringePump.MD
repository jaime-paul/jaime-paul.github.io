---
title: "Syringe Pump"
excerpt: "A motor-driven pump that can deliver a range of flow rates."
header:
  teaser: /assets/img/Syringe Pump Img.png
gallery:
  - image_path: assets/img/syringe-pump-blueprint1.jpg
  - image_path: assets/img/syringe-pump-blueprint2.jpg
  - image_path: assets/img/syringe-pump-blueprint3.jpg
  - image_path: assets/img/syringe-pump-blueprint4.jpg
  - image_path: assets/img/syringe-pump-blueprint5.jpg
  - image_path: assets/img/syringe-pump-blueprint6.jpg


---

## About

The Syringe Pump a motor-driven pump that can deliver a range of flow rates. The goal is for a lead screw to turn and as a nut traverses the screw, a plunger is pushed forward, which ejects a proportional amount of liquid contained in the syringe. The materials provided were a stepper motor, lead screw, motor coupler, linear rod, aluminum extrusion, power supply, arduino, stepper driver, breadboard, latching push button, limit switch, LED light, and various electrical materials to connect components. Syringe pumps are typically used in laboratory or medical settings where they can dispense fluids at a precise rate. Syringe pumps only require a handful of parts and depend on simple electronic control systems, but can still cost several hundred dollars to purchase. This means that being able to design, 3D print, and program a syringe pump can save hundreds of dollars.

## Operating Instructions

To begin, the desired syringe (10ml or 20ml) must be filled with liquid and its flange must be inserted into the syringe slot on the stationary end support. The syringe must be oriented so the plunger end lies flush against the rounded carriage face, and the nozzle of the syringe is pointed away from the motor. Once securely inserted, the pump may be plugged into an outlet. The motor which powers the pump, the microcontroller and the indicator lights all require a power source to function. That’s why once plugged in, the tri-color LED embedded in the front face of the box will turn on (it will be yellow by default, indicating the pumps paused state). The latching button directly left of the LED can be pressed to start the pump, which will cause the LED to turn green indicating the pump is running and dispensing liquid. If pressed again, the light will turn yellow (for paused), and then green again once restarted. Once all of the liquid in the syringe has been dispensed, a limit switch will be triggered and the light will turn red, indicating an empty syringe that must be refilled. To refill when red, first pause the pump by ensuring the latching button is pressed, remove the empty syringe from the slot, press-and-hold the button on the far left to rewind the pump (when rewinding the LED will turn purple), and reinsert a filled syringe into the slot (in the same manner as before). If the pump has been rewinded too far, simply press-and-hold the button directly right of the reverse button to move the pump forward (as indicated by a blue LED). Once a new, full, syringe has been reinserted, press the latching button once more to unpause the pump and achieve a green light, and watch it run.

## CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b602811d43a06ce7ad3a361?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

## Off The Shelf Parts

| Component Name             | 
| ---------------------------| 
| Linear-Rod-8mmx200mm       |
| Bread Board                |
| Arduino UNO                |
| F688ZZ-Flanged-Ball-Bearing|
| LED 4 pin RGB v1           |
| LM8UU-Linear-Bearing       |
| LED 4 pin RGB v1           |
| Lead-Screw-TR8x8x250mm     |
| Lock-Collar-Lead-Screw     | 
| meanwell_RD-65A            |
| V-Slot 20x40x350           |
| Push Button Red v9 10mm    |
| Nut-tr8x8-4                |
| NEMA-17-Motor              |
| M5x8mm-Bolt                |
| M5-Tee-Nut                 |
| M3x8-Thread-Forming-Screw  |
| M3x10mm-Bolt               |
| Lock-Collar-Linear-Rod     |


## Blueprints

{% include gallery caption="Syringe Pump Blueprints Gallery" %}

## Arduino Code

// Motor control pins into the Arduino
#define STEP_PIN 4
#define DIR_PIN 3

// Input pins into the Arduino
#define LATCHING_BUTTON_PIN 5
#define LIMIT_SWITCH_PIN 6

// LED pins - input pins into the Arduino
#define LED_RED_PIN 8
#define LED_GREEN_PIN 9
#define LED_BLUE_PIN 10

// Extra credit input pins into the Arduino (non-latching button inputs)
#define CCW_PIN 11 // Counterclockwise
#define CW_PIN 12  // Clockwise

float largeSyringeDiameter = 18.7; // Measured internal diameter of syringe
float smallSyringeDiameter = 14.6;

float flowRate = 5; // mL/min [EDIT THIS VALUE to change pump speed]
float syringeDiameter = smallSyringeDiameter; // smallSyringeDiameter for 10 mL, largeSyringeDiameter for 20 mL
float distancePerRevolution = 8.0; // Lead screw lead
float stepsPerRevolution = 3200; // 3200 (16-step microstepping)

#include <AccelStepper.h>

AccelStepper stepper(AccelStepper::DRIVER, 4, 3); // Uses STEP and DIR pin input values

void setup() // Initial setup: configuring pins as INPUT_PULLUP/OUTPUT
{
  stepper.setMaxSpeed(1000); // Loop only runs once, so this initializes the value
  calculateStepperSpeed();

  pinMode(LED_RED_PIN, OUTPUT);
  pinMode(LED_GREEN_PIN, OUTPUT);
  pinMode(LED_BLUE_PIN, OUTPUT);

  pinMode(LATCHING_BUTTON_PIN, INPUT_PULLUP);
  pinMode(LIMIT_SWITCH_PIN, INPUT_PULLUP);

  setColor(0, 255, 0); // Green initially

  pinMode(CCW_PIN, INPUT_PULLUP);
  pinMode(CW_PIN, INPUT_PULLUP);
}

void loop() // Runs infinitely, constantly checking for changes in button states
{
  if (digitalRead(LATCHING_BUTTON_PIN) == LOW &&
      digitalRead(LIMIT_SWITCH_PIN) == HIGH)
  {
    // If latching button is pressed, run the pump
    calculateStepperSpeed();
    stepper.runSpeed();
    setColor(0, 255, 0); // Green
  }

  if (digitalRead(LATCHING_BUTTON_PIN) == HIGH &&
      digitalRead(LIMIT_SWITCH_PIN) == HIGH)
  {
    // If latching button is pressed again, pause the pump
    setColor(255, 50, 0); // Yellow

    if (digitalRead(CCW_PIN) == LOW)
    {
      // If paused and the counterclockwise button is pressed
      setColor(255, 0, 255); // Purple - CCW / reverse for easy reset
      stepper.setSpeed(900);
      stepper.runSpeed();
    }

    if (digitalRead(CW_PIN) == LOW)
    {
      // If the clockwise button is pressed
      setColor(0, 0, 255); // Blue - CW / forward if reversed too far
      stepper.setSpeed(-900); // Negative because this is the forward direction
      stepper.runSpeed();
    }
  }

  if (digitalRead(LATCHING_BUTTON_PIN) == LOW &&
      digitalRead(LIMIT_SWITCH_PIN) == LOW)
  {
    // If the limit switch is triggered, stop the pump because it is empty
    setColor(255, 0, 0); // Red
  }

  if (digitalRead(LATCHING_BUTTON_PIN) == HIGH &&
      digitalRead(CCW_PIN) == LOW)
  {
    // Pause after limit switch is triggered, then allow reversal
    if (digitalRead(CCW_PIN) == LOW)
    {
      stepper.setSpeed(900);
      stepper.runSpeed();
    }
  }
}

void setColor(int redValue, int greenValue, int blueValue)
{
  // Simple set-color function to make setting RGB values easier in void loop
  analogWrite(LED_RED_PIN, redValue);
  analogWrite(LED_GREEN_PIN, greenValue);
  analogWrite(LED_BLUE_PIN, blueValue);
}

void calculateStepperSpeed()
{
  // Calculate stepper speed based on the desired flow rate
  // See the calculation section for an explanation

  float syringeArea = 3.14159 * pow(syringeDiameter / 2.0, 2);

  float flowRateMmCubed = flowRate * 1000.0;

  float linearSpeed = flowRateMmCubed / syringeArea;

  float stepperSpeed =
      (linearSpeed / distancePerRevolution) *
      stepsPerRevolution / 60.0; // Steps per second

  stepper.setSpeed(-stepperSpeed); // Negative because this is the forward direction
}




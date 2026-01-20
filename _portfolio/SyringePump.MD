---
title: "Syringe Pump"
excerpt: "A motor-driven pump that can deliver a range of flow rates."
header:
  teaser: /assets/img/Large-Format-3D-Printer-Thumbnail.png
gallery:
  - image_path: assets/img/syringe-pump-blueprint1.jpg
  - image_path: assets/img/syringe-pump-blueprint2.jpg
  - image_path: assets/img/syringe-pump-blueprint3.jpg


---

## About

The Syringe Pump a motor-driven pump that can deliver a range of flow rates. The goal is for a lead screw to turn and as a nut traverses the screw, a plunger is pushed forward, which ejects a proportional amount of liquid contained in the syringe. The materials provided were a stepper motor, lead screw, motor coupler, linear rod, aluminum extrusion, power supply, arduino, stepper driver, breadboard, latching push button, limit switch, LED light, and various electrical materials to connect components. Syringe pumps are typically used in laboratory or medical settings where they can dispense fluids at a precise rate. Syringe pumps only require a handful of parts and depend on simple electronic control systems, but can still cost several hundred dollars to purchase. This means that being able to design, 3D print, and program a syringe pump can save hundreds of dollars.

## Operating Instructions

To begin, the desired syringe (10ml or 20ml) must be filled with liquid and its flange must be inserted into the syringe slot on the stationary end support. The syringe must be oriented so the plunger end lies flush against the rounded carriage face, and the nozzle of the syringe is pointed away from the motor. Once securely inserted, the pump may be plugged into an outlet. The motor which powers the pump, the microcontroller and the indicator lights all require a power source to function. That’s why once plugged in, the tri-color LED embedded in the front face of the box will turn on (it will be yellow by default, indicating the pumps paused state). The latching button directly left of the LED can be pressed to start the pump, which will cause the LED to turn green indicating the pump is running and dispensing liquid. If pressed again, the light will turn yellow (for paused), and then green again once restarted. Once all of the liquid in the syringe has been dispensed, a limit switch will be triggered and the light will turn red, indicating an empty syringe that must be refilled. To refill when red, first pause the pump by ensuring the latching button is pressed, remove the empty syringe from the slot, press-and-hold the button on the far left to rewind the pump (when rewinding the LED will turn purple), and reinsert a filled syringe into the slot (in the same manner as before). If the pump has been rewinded too far, simply press-and-hold the button directly right of the reverse button to move the pump forward (as indicated by a blue LED). Once a new, full, syringe has been reinserted, press the latching button once more to unpause the pump and achieve a green light, and watch it run.

## CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b602811d43a06ce7ad3a361?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

## Off The Shelf Parts

| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

{% include gallery caption="Syringe Pump Blueprints Gallery" %}

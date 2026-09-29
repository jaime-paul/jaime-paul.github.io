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

This pair of needle-nose pliers utilizes print-in-place 3D printed parts. These pliers are capable of picking up through hole resistors. They utilize a spring component which allows them to return to an open position when not in use. Print-in-place is a unique benefit to 3D printing that allows you to create multiple components that work immediately after they come off the print bed, without requiring additional assembly. Prints that use print-in-place use multiple different methods of hinges and linkages to connect the various parts together.

Print-in-place has many applications beyond my project. It can be used to create functional mechanisms such as pliers, as well as children's toys that require some sense of flexibility. For example, this print-in-place articulated snake puzzle uses multiple connected sections to create a flexible toy. Print-in-place can also be used for functional tools, such as pliers which I created for this project, which use a single printed structure to create a working pair of pliers.

One of the most useful applications of print-in-place is the ability to create hinges and other moving joints. These mechanisms heavily depend on clearance between parts which makes the materials that you choose to print with all the more important. PLA and TPU can work well together when different levels of flexibility are needed. PLA provides a rigid structure, while TPU can be used for flexible hinges or joints. This combination allows the rigid portions of a design to maintain their shape while the TPU provides movement that PLA alone would not be able to provide.


## Operating Instructions

To begin, the desired syringe (10ml or 20ml) must be filled with liquid and its flange must be inserted into the syringe slot on the stationary end support. The syringe must be oriented so the plunger end lies flush against the rounded carriage face, and the nozzle of the syringe is pointed away from the motor. Once securely inserted, the pump may be plugged into an outlet. The motor which powers the pump, the microcontroller and the indicator lights all require a power source to function. That’s why once plugged in, the tri-color LED embedded in the front face of the box will turn on (it will be yellow by default, indicating the pumps paused state). The latching button directly left of the LED can be pressed to start the pump, which will cause the LED to turn green indicating the pump is running and dispensing liquid. If pressed again, the light will turn yellow (for paused), and then green again once restarted. Once all of the liquid in the syringe has been dispensed, a limit switch will be triggered and the light will turn red, indicating an empty syringe that must be refilled. To refill when red, first pause the pump by ensuring the latching button is pressed, remove the empty syringe from the slot, press-and-hold the button on the far left to rewind the pump (when rewinding the LED will turn purple), and reinsert a filled syringe into the slot (in the same manner as before). If the pump has been rewinded too far, simply press-and-hold the button directly right of the reverse button to move the pump forward (as indicated by a blue LED). Once a new, full, syringe has been reinserted, press the latching button once more to unpause the pump and achieve a green light, and watch it run.

## CAD Model

<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b602811537fdbb62fa2189a?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

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

<script>
fetch('/assets/img/arduino_code.txt')
  .then(response => response.text())
  .then(code => {
    document.getElementById('arduino-code').textContent = code;
  });
</script>

<style>
#arduino-code {
  display: block;
  background-color: #f6f8fa;
  padding: 20px;
  border-radius: 6px;
  overflow-x: auto;
  white-space: pre;
  font-family: monospace;
  font-size: 14px;
  line-height: 1.5;
  color: #24292f;
}
</style>



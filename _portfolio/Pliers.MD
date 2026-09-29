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

Print-in-place has many applications beyond my project. It can be used to create functional mechanisms such as pliers, as well as children's toys that require some sense of flexibility. For example, [this print-in-place](https://cults3d.com/en/3d-model/game/snakeinplace-print-in-place-and-articulated-puzzle-toy) articulated snake puzzle uses multiple connected sections to create a flexible toy. Print-in-place can also be used for functional tools, such as pliers which I created for this project, which use a single printed structure to create a working pair of pliers.

One of the most useful applications of print-in-place is the ability to create hinges and other moving joints. These mechanisms heavily depend on clearance between parts which makes the materials that you choose to print with all the more important. PLA and TPU can work well together when different levels of flexibility are needed. PLA provides a rigid structure, while TPU can be used for flexible hinges or joints. This combination allows the rigid portions of a design to maintain their shape while the TPU provides movement that PLA alone would not be able to provide.


## Process

The pliers are made up of three components, two pliers and a spring component. The two pliers are printed using PLA. This creates accurate, rigid, and detailed components that are able to securely pick up various small objects. These two components are joined together through a keyed slip-joint pivot. One plier has an extrusion with a flattened pin on the top. The other plier has a circular cut with two small extrusions on the side, which allow the other plier to slot in and stay on. This allows the two pliers to move around the pivot while still keeping them connected.

The third component is the spring. This component is made from TPU because of its flexible properties. The component has two dovetails on either end to allow it to slot into the two pliers. The material forms a ninety-degree angle, which allows the spring to flex when the pliers are squeezed and return the pliers to their original position when released.

Throughout the design process, I had to consider the dimensions of the pivot, the clearances between the two pliers, and the dimensions of the spring. The components needed to be close enough together to stay connected while still having enough clearance to move freely after printing. I also had to make sure the spring was flexible enough to allow the pliers to open and close without being too weak.

## CAD Model

<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH90d2dQT28d5b602811c00167e441a890c9?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

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



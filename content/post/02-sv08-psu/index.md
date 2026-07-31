---
title: Sovol SV08 Power Supply & Electronics Bay Fan Upgrade
date: 2025-04-22
draft: false
showAuthor: false
showReadingTime: false
showWordCount: false
toc: true
tags:
  - 3dprinting
  - sv08
image: featured.webp

---
{{< youtube id="bB7REX9gJ0E" label="Sovol SV08 Power Supply & Electronics Bay Fan Upgrade" >}}

## Overview
In today’s video, we’re diving into some upgrades on the Sovol SV08 3D printer — specifically focusing on the electronics bay.\
We're swapping out the stock power supply, with a more powerful alternative that has an active fan. Plus, we’ll be replacing the control board fan and adding a dedicated fan for the MOSFET that controls the bed heating to help keep everything running at lower temperatures.

Whether you're modding your SV08 for performance, silence, or just love to tinker, this upgrade is a solid step towards a cooler, more reliable machine.

## printer.cfg
Basic Fan Configuration in printer.cfg [fan_generic fanX] # mosfet fan pin: PA6 max_power: 1.0 3D 

````text
[fan_generic fanX] # mosfet fan
pin: PA6 max_power: 1.0
````

## 3D printed parts
Printed Parts PSU Mount: [Printables](https://www.printables.com/model/1196209-sv08-larger-power-supply-mounting-bracket)  
Control board 8010 Fan: [Printables](https://www.printables.com/model/1104389-sovol-sv08-elecronics-8010-fan-mount)  
Mosfet 8010 Fan: [Printables](https://www.printables.com/model/1268452-sovol-sv08-mosfet-fan-bracket)  
## Parts
Meanwell LRS-350 Power Supply: [Amazon](https://amzn.to/4jqqeYQ) * / [AliExpress](https://s.click.aliexpress.com/e/_oCkY6Wd) *  
2x 8010 24v Fans: [Amazon](https://amzn.to/4jlEvX4) * /  [AliExpress](https://s.click.aliexpress.com/e/_oEnxUYZ) *  

## Support me!
You like the content and want to support me? [Buy me some ABS!](https://ko-fi.com/andystechlab)  

**Some of the stuff i use:**\
PLA Filament: [Amazon](https://amzn.to/3Vauu4n) *  
ABS Filament: [Amazon](https://amzn.to/4lzb316) *  
Filament Dryer: [Amazon](https://amzn.to/42NVXxg) *  

*This link is an affiliate link, which means I may earn a commission at no extra cost to you.

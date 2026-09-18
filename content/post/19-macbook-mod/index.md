---
title: MacBook Air 2017 Cooling Mod
date: 2026-09-18
publishDate: 2026-09-17T19:01:00+02:00
draft: false
showAuthor: false
showReadingTime: false
showWordCount: false
toc: true
tags:
  - diy
  - Linux
image: featured.webp

---
{{< youtube id="-wjMsOjrkSU" label="MacBook Air 2017 Cooling Mod" >}}

## Overview
The 2017 MacBook Air isn't exactly known for having an overpowered cooling system. Under sustained CPU load, temperatures can climb quickly and the fan has to work hard to keep the system under control.

So I wanted to find out how much the cooling can actually be improved — starting with the obvious solution and then taking things a little further.

In this experiment, I first establish a baseline with the MacBook in its original configuration. I then replace the old thermal paste and repeat the exact same stress test to see how much basic maintenance alone can improve the thermals.

After that, things get more interesting.

I modify the bottom cover by adding ventilation holes directly underneath the fan, giving it an additional path to pull in fresh air. Finally, I test whether raising the MacBook slightly off the desk improves airflow through those new vents even further.

The video documents the complete modification and compares all four configurations under the same workload:

- Stock MacBook Air
- Fresh thermal paste
- Fresh thermal paste + ventilation holes
- Ventilation holes + additional clearance underneath the MacBook

If you're curious whether drilling holes into an old MacBook actually improves its cooling — and whether it's worth doing at all — you can watch the complete experiment in the video above.
___
## Tools used
* Bit Set(P5 & T5) - [Amazon](https://link.amazon/B0fPmtKha) *  
* Center Punch - [Amazon](https://link.amazon/B03w5UQQX) *  
* Drill
* 2,5mm Drill Bit
* Labelprinter for Stencil - [Amazon](https://link.amazon/B00zn6XuO) *  
<img src="drill-me-daddy.png" style="width: 377px; max-width: 100%; height: auto;" alt="">\
(Scale to ~40mm)
___
## Commands
Install(specific for Fedora):
```
sudo dnf install stress-ng -y
```

Stresstest:
```
stress-ng --cpu 0 --cpu-method matrixprod --timeout 10m --metrics-brief
```

Temperature Sensors:
```
watch -n 1 sensors
```
___
## Support me!
You like the content and want to support me? [Buy me some ABS!](https://ko-fi.com/andystechlab)  
Or buy something with my [affiliate links](https://andystechlab.dev/product-links/) with no exra cost!  

**Some of the stuff i use:**\
PLA Filament: [Amazon](https://amzn.to/3Vauu4n) *  
ABS Filament: [Amazon](https://amzn.to/4lzb316) *  
Filament Dryer: [Amazon](https://amzn.to/42NVXxg) *  

*This link is an affiliate link, which means I may earn a commission at no extra cost to you.

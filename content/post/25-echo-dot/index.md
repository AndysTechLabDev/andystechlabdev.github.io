---
title: Rooting an Echo Dot 3 for Local Home Assistant Voice Control
date: 2026-10-30
publishDate: 2026-10-30T18:30:00+01:00
draft: false
showAuthor: false
showReadingTime: false
showWordCount: false
toc: true
tags:
image: featured.webp

---
{{< youtube id="a5bRPBtgw-U" label="Rooting an Echo Dot 3 for Local Home Assistant Voice Control" >}}

## Overview

An Echo Dot can become a Home Assistant voice satellite without relying on Amazon’s cloud for voice commands. I tried it with the **Echo Dot 3 from 2018**, using a Linux computer, a USB cable soldered directly to the board, and an open-source project.
___
## How it works

The Echo Dot has no USB socket, so the project uses test pads on the board for the USB data connection. After rooting the device, its Alexa client is replaced with software that connects it to Home Assistant as an ESPHome device.

The project’s guided setup handles much of the process, but still requires some manual steps. In my case, I downloaded a few files, entered my Wi-Fi details, and ran the setup from Fedora Linux.
___
### Credit where it's due

A big thanks to **Roger Ortiz** for his research and work on unlocking and rooting Amazon Echo devices. His contributions laid important groundwork for projects like Echo Dot Assist, making it possible to give these devices a second life outside Amazon's ecosystem. It's worth recognizing the people doing the low-level research that makes projects like this possible in the first place.

You can find more about his work in his [XDA Developers thread](https://xdaforums.com/t/unlock-root-twrp-unbrick-amazon-echo-dot-3rd-gen-2018-donut.4801400/).  
___
## Shell Commands
Clone the repo from Github:
```
git clone https://github.com/Gamer92000/echo-dot-assist.git  
```

Change the directory:
```
cd echo-dot-assist
```

Make the script executeable:
```
chmod +x scripts/setup.sh
```

Run the script:
```
scripts/setup.sh
```

___
## Check your model first

This method supports the **2018 Echo Dot 3, model D9N29T**. It does not support the later 2019–2020 refresh or the Echo Dot with a clock. Check the model before opening the device.

The repository says the software was created with AI assistance and has not been audited. Rooting can also brick the Echo, so read the project’s own instructions and risk notes before starting.
___
## Testing it with Home Assistant

After rooting, Home Assistant discovered the Echo as an ESPHome device. I then configured an Assist pipeline and tried local voice commands.

Whisper was slow on my Home Assistant server, which runs on a Celeron mini PC with a virtual machine limited to one CPU core and three gigabytes of RAM. I switched to Speech-to-Phrase, which handled common smart-home commands more quickly, though the server still limits the experience.

This project gives a supported Echo Dot a new purpose and keeps the voice assistant local. The soldering and rooting process require care, and the final response speed depends on the Home Assistant hardware.
___
## Links

- [Echo Dot Assist on GitHub](https://github.com/Gamer92000/echo-dot-assist)  
- [Home Assistant: fully local voice assistant](https://www.home-assistant.io/voice_control/voice_remote_local_assistant/)  
- [My Fedora MacBook video]([ADD-VIDEO-LINK](https://youtu.be/R6-nGdcRxSU))  
- [Roger Ortiz's Echo unlocking work on XDA Developers](https://xdaforums.com/t/unlock-root-twrp-unbrick-amazon-echo-dot-2nd-gen-2016-biscuit.4761416/)  
___
## Support me!
You like the content and want to support me? [Buy me some ABS!](https://ko-fi.com/andystechlab)  
Or buy something with my [affiliate links](https://andystechlab.dev/product-links/) with no exra cost!  

**Some of the stuff i use:**\
PLA Filament: [Amazon](https://amzn.to/3Vauu4n) *  
ABS Filament: [Amazon](https://amzn.to/4lzb316) *  
Filament Dryer: [Amazon](https://amzn.to/42NVXxg) *  

*This link is an affiliate link, which means I may earn a commission at no extra cost to you.

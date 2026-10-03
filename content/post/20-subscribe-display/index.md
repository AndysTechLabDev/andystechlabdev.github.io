---
title: Building a Subscriber Display with a Tiny ESP32
date: 2026-09-29
publishDate: 2026-09-29T18:57:00+02:00
draft: false
showAuthor: false
showReadingTime: false
showWordCount: false
toc: true
tags:
  - diy
image: featured.webp

---
{{< youtube id="77pNLjQWU8E" label="Building a Subscriber Display with a Tiny ESP32" >}}

## Overview

For this project, I built a compact **YouTube Subscriber Display** that shows the current subscriber count of a YouTube channel directly on a small screen.

The idea was simple: instead of opening YouTube Studio just to check the latest numbers, why not have them permanently visible on the desk?

The display is based on an **ESP32-C3 SuperMini** and a narrow **2.79" IPS display** with a resolution of 142 × 428 pixels. The ESP32 connects to Wi-Fi and periodically retrieves the latest channel information using the **YouTube Data API**.
___
## More Than Just a Subscriber Counter

I wanted the device to be easy to use without having to modify and upload the firmware every time something changes.

For that reason, the Subscriber Display includes its own **web-based configuration interface**. Wi-Fi credentials, YouTube channel, API key, display appearance, brightness, update interval and several other options can be configured directly from a browser.

On the first startup, the device creates its own Wi-Fi network for the initial configuration. Once connected to your home network, the settings can be accessed again through the local web interface.

The display itself can show the **subscriber count, channel name, YouTube logo and current time**, with several options to customize its appearance.

Two physical buttons provide some additional controls directly on the device, including switching between different subscriber number formats and using the ESP32's sleep modes.
___
## Build Your Own

The complete project is available on **GitHub**.

There you'll find the source code together with the wiring diagram, pin assignments, required Arduino libraries, Arduino IDE settings and detailed setup instructions.

___
## Hardware Used

The project only requires a handful of components:

- **ESP32-C3 SuperMini** - [AliExpress](https://s.click.aliexpress.com/e/_c3POTIgN) *  
- **2.79" 142 × 428 NV3007 IPS Display** - [AliExpress](https://s.click.aliexpress.com/e/_c4c5s8nL) *  
- **2 × Push Buttons** - [AliExpress](https://s.click.aliexpress.com/e/_c30Kgqcl) *  
- **24AWG Wire** - [AliExpress](https://s.click.aliexpress.com/e/_c3e0JJFf) *  
- **Dupont Connector Kit** - [AliExpress](https://de.aliexpress.com/item/1005001988527603.html?spm=a2g0o.detail.pcDetailTopMoreOtherSeller.11.22d6AGlmAGlm5y&gps-id=pcDetailTopMoreOtherSeller&scm=1007.40050.354490.0&scm_id=1007.40050.354490.0&scm-url=1007.40050.354490.0&pvid=96c7a000-a6a7-46e3-8e42-9bf05e04a63b&_t=gps-id%3ApcDetailTopMoreOtherSeller%2Cscm-url%3A1007.40050.354490.0%2Cpvid%3A96c7a000-a6a7-46e3-8e42-9bf05e04a63b%2Ctpp_buckets%3A668%232846%238116%232002&pdp_ext_f=%7B%22order%22%3A%22106%22%2C%22spu_best_type%22%3A%22price%22%2C%22eval%22%3A%221%22%2C%22sceneId%22%3A%2230050%22%2C%22fromPage%22%3A%22recommend%22%7D&pdp_npi=6%40dis%21EUR%213.73%213.73%21%21%214.14%214.14%21%400b88ad2b17904559606663215e1285%2112000018327329226%21rec%21AT%211878345755%21X%211%210%21n_tag%3A-29919%3Bd%3A9a35da8f%3Bm03_new_user%3A-29895&utparam-url=scene%3ApcDetailTopMoreOtherSeller%7Cquery_from%3A%7Cx_object_id%3A1005001988527603%7C_p_origin_prod%3A)  
___
## Tools Used

For the build, I used:

- Soldering iron - [AliExpress](https://s.click.aliexpress.com/e/_c3W6KI1J) *  
- Wire stripper - [AliExpress](https://s.click.aliexpress.com/e/_c3zIVuKt) *  
- Heat Set Inserts - [AliExpress](https://s.click.aliexpress.com/e/_c4dcIgDR) *  

The software setup and configuration are documented in the GitHub repository, so I won't duplicate all the technical details here.

If you want to see the Subscriber Display in action and get a closer look at the build, check out the video at the top of this post.
___

## 3D Printed Parts

* [Printables](https://www.printables.com/model/1859082-esp32-c3-subscriber-counter)  

___
## Wiring Diagram
<img src="wiring-diagram-1.png" style="width: 100%; max-width: 100%; height: auto;" alt="">

___
## Sources
* Get the Code on [Github](https://github.com/AndysTechLabDev/SubscriberDisplay)  
* [Arduino IDE](https://www.arduino.cc/en/software/)  
* [YouTube API](https://console.cloud.google.com/marketplace/product/google/youtube.googleapis.com)  
* [DIY Heat Insert Press](https://youtu.be/klOXuKuPEaU)  
___
## Support me!
You like the content and want to support me? [Buy me some ABS!](https://ko-fi.com/andystechlab)  
Or buy something with my [affiliate links](https://andystechlab.dev/product-links/) with no exra cost!  

**Some of the stuff i use:**\
PLA Filament: [Amazon](https://amzn.to/3Vauu4n) *  
ABS Filament: [Amazon](https://amzn.to/4lzb316) *  
Filament Dryer: [Amazon](https://amzn.to/42NVXxg) *  

*This link is an affiliate link, which means I may earn a commission at no extra cost to you.

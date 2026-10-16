---
title: Building a Raspberry Pi Mini PC with a SATA SSD
date: 2026-10-17
publishDate: 2026-09-17T18:30:00+02:00
draft: false
showAuthor: false
showReadingTime: false
showWordCount: false
toc: true
tags:
  - homelab
  - RaspberryPi
  - 3dprinting
image: featured.webp

---
{{< youtube id="Vs9_69Owp0k" label="# Building a Raspberry Pi Mini PC with a SATA SSD and a Custom 3D Printed Case" >}}

## Overview
The Raspberry Pi is one of those devices that always seems to find its way into my projects. Whether it's for experimenting with Linux, running small services, or building something for my homelab, there's almost always a use for one.

However, one thing I've never been particularly happy with is the storage.

While microSD cards are convenient and perfectly fine for many applications, I've had some bad experiences with them over the years. I eventually switched to USB flash drives for some of my projects, but those weren't the solution I was looking for either.

For my next Raspberry Pi project, I wanted to try something a little different: a proper SSD.

Instead of going with another microSD card or flash drive, I decided to use a 2.5-inch SATA SSD connected through USB 3.0.

But that introduced another challenge. I needed a way to fit the Raspberry Pi, the SSD, and the necessary connections into a single enclosure.

Since I couldn't find a case that matched what I had in mind, I decided to design and 3D print my own.

The result is a compact Raspberry Pi mini PC case with a textured outer shell, a removable internal tray, and all the important connections accessible from the back.

In this article, I'll take a closer look at the design, the components I used, and how everything fits together.
___
## Why a 2.5-inch SATA SSD?
There are several ways to connect external storage to a Raspberry Pi, and a SATA SSD is certainly not the most compact option available.

For the Raspberry Pi 4, there are also M.2 expansion boards that connect through USB. These can be a great option if you're looking for a smaller overall footprint.

However, after comparing the available options, I found that a basic 2.5-inch SATA SSD combined with a USB-to-SATA adapter was the more affordable solution for my build.

I purchased the cheapest suitable SATA SSD I could find and paired it with a simple USB 3.0 adapter.

This approach has a few advantages:

- No special expansion board required
- Standard SATA SSDs are easy to find
- The SSD can be connected using one of the Pi's USB 3.0 ports
- The same storage setup can be used with a Raspberry Pi 4 or Raspberry Pi 5
- The SSD can easily be replaced without changing the overall design

Of course, a 2.5-inch SSD takes up more physical space than an M.2 drive.

But since I was planning to design my own enclosure anyway, I didn't mind the additional size.

In fact, it gave me an opportunity to make something that looks a little more like a traditional desktop PC.
___
## Designing the Case in FreeCAD

My goal wasn't to create the smallest possible Raspberry Pi enclosure.

Instead, I wanted something that would look good on a desk, keep the hardware protected, and make assembly and future maintenance as straightforward as possible.

I started designing the enclosure in FreeCAD with a few requirements in mind.

**Mini PC aesthetics**

Rather than leaving the Raspberry Pi and SSD exposed, I wanted a clean enclosure that resembles a small desktop PC.

**Easy assembly and maintenance**

The case should be easy to put together without complicated mounting mechanisms or an excessive number of screws.

It should also be possible to remove the hardware without having to completely disassemble the enclosure.

**Clean rear connections**

One of the things I wanted to avoid was having cables coming out of different sides of the case.

To make the finished system feel more like a regular mini PC, I designed the rear of the enclosure to accommodate panel-mount extensions for USB-A, Ethernet, and USB-C.

**Support for both Raspberry Pi 4 and Raspberry Pi 5**

Although this build uses a Raspberry Pi 4, the enclosure was designed with compatibility for the Raspberry Pi 5 in mind as well.
___
### A Three-Part Design

The finished enclosure consists of three separate 3D printed components.

**1. Outer Shell**

The outer shell forms the main body of the enclosure and gives the mini PC its overall appearance.

It also includes the rear openings for the external connections and accommodates the internal sliding tray.

**2. Sliding Tray**

The sliding tray is the main mounting platform for the hardware.

Both the Raspberry Pi and the 2.5-inch SATA SSD are attached to this part, allowing the entire assembly to slide into the outer shell.

This makes the case considerably easier to assemble and maintain compared to a design where everything needs to be mounted inside a closed enclosure.

**3. Front Grill**

The front grill is a separate printed component that fits into the front of the outer shell.

Printing it separately allowed me to experiment with different colors without having to reprint the entire enclosure.

Once the final color was chosen, the grill was glued into place.
___
## 3D Printing the Enclosure

One of the design details I'm particularly happy with is the surface finish of the outer shell.

I decided to print it using fuzzy skin.

This adds a subtle texture to the surface and makes the enclosure look less like a typical FDM 3D print. It also helps disguise some of the visible layer lines.

For the front grill, I printed three different versions: grey, white, and black.

All three worked with the design, but I eventually settled on black.

In my opinion, the darker front grill gives the enclosure a cleaner and slightly more professional appearance.

Because the grill is printed separately, experimenting with colors was straightforward during the prototyping stage.

The final grill is permanently installed using adhesive.
___
### Printing Tips

If you're planning to print this enclosure yourself, there are a few things worth keeping in mind.

**Fuzzy skin:** A subtle fuzzy skin texture works particularly well on the outer shell, but the exact appearance will depend on your slicer settings and filament.

**Dimensional accuracy:** The sliding tray needs to fit properly into the outer shell. Make sure your printer is reasonably well calibrated, especially if you notice tight clearances.

**Heat-set inserts:** The Raspberry Pi mounting points are designed to use threaded inserts, so make sure you have compatible inserts available before starting the assembly.

**Test fitting:** It's worth checking that all printed components and panel-mount connectors fit correctly before permanently gluing the front grill or completing the final assembly.
___
## Hardware and Assembly

Once all the printed parts were ready, I could start assembling the mini PC.

The process is fairly straightforward, thanks to the sliding tray design.
___
### Mounting the SSD

The 2.5-inch SATA SSD is attached directly to the sliding tray using M3 screws.

This keeps it securely positioned inside the enclosure without requiring an additional mounting bracket.
___
### Installing the Heat-Set Inserts

For the Raspberry Pi mounting points, I decided to use heat-set inserts.

These are small threaded metal inserts that are melted into the plastic using heat.

They provide durable metal threads, which is particularly useful for parts that may need to be assembled and disassembled more than once.

After installing the inserts in the sliding tray, the Raspberry Pi can be secured using M3 screws.

I actually built my own heat-set insert press for projects like this, which makes installing inserts much easier and more consistent.

If you're interested in building one yourself, I've covered the entire process in a separate video.

**Related project:** [My DIY Heat-Set Insert Press](https://youtu.be/klOXuKuPEaU)  
___
### Connecting the SSD

With the Raspberry Pi and SSD mounted, the next step is connecting the storage.

The SATA SSD uses a USB-to-SATA adapter, which connects directly to one of the Raspberry Pi's USB 3.0 ports.

This keeps the setup simple and avoids the need for a dedicated storage expansion board.
___
### Installing the Rear Connections

To keep the enclosure looking clean, I incorporated mounting points for several panel-mount extensions.

These provide external access to the connections without having to plug cables directly into the Raspberry Pi inside the case.

The rear panel includes connections for:
- USB-A
- Ethernet (RJ45)
- USB-C

The extensions are connected internally to the appropriate Raspberry Pi ports.

This arrangement makes it much easier to connect the finished mini PC to power, networking, and peripherals while keeping the front and sides of the enclosure free from exposed connectors.
___
### Final Assembly

Once everything is mounted and connected, the complete internal assembly can be inserted into the outer shell.

The sliding tray fits into the enclosure and is secured using just two M3 screws.

And that's it.

The Raspberry Pi, SSD, and internal connections are now contained within a single compact enclosure.

If I ever need to access the hardware, I can simply remove the two screws and slide the tray back out.
___
## The Finished Raspberry Pi Mini PC

I'm really happy with how this project turned out.

The combination of the textured outer shell, black front grill, and rear-mounted connections gives the enclosure the appearance I was aiming for.

Although it isn't the smallest Raspberry Pi case, that was never the goal.

I wanted something practical that would accommodate a standard 2.5-inch SATA SSD while still looking like a proper little desktop PC.

The sliding tray also makes the design convenient to work with, especially when it comes to replacing components or making changes later on.

And because the enclosure was designed to support both the Raspberry Pi 4 and Raspberry Pi 5, it should also be useful for future projects.
___
## What's Next?

This project was mainly about getting the hardware ready.

I haven't covered the operating system, software configuration, or what I'm actually planning to use this Raspberry Pi for.

That's intentional.

I have a specific project in mind, and I'll be covering that in a separate video and blog post.
For now, I wanted to focus on the enclosure, the design decisions, and the hardware assembly.

If you're interested in Raspberry Pi projects, 3D printing, Linux, or homelab setups, make sure to check out the video at the top of this article.
___
## Downloads and Resources

Here are the relevant files, components, and additional resources for this project.

### 3D Models

- **Raspberry Pi Mini PC Case:** [Printables](https://www.printables.com/model/1879181-raspberry-pi-45-mini-pc-case)  
 
### Hardware

- **Raspberry Pi 4:** [Amazon](https://link.amazon/B0aTFcXMT) *  
- **2.5-inch SATA SSD:** [Amazon](https://link.amazon/B07L9vsD9) *  
- **USB 3.0 to SATA Adapter:** [Amazon](https://link.amazon/B0gJobTlE) *  
- **USB-A Panel-Mount Extension:** [Amazon](https://link.amazon/B09iurJFC) *  
- **Ethernet / RJ45 Panel-Mount Extension:** [Amazon](https://link.amazon/B0cWihpiU) *  
- **USB-C Panel-Mount Extension:** [Amazon](https://link.amazon/B075GKQEH) / [AliExpress](https://s.click.aliexpress.com/e/_c44F9HOz) *  
- **M3 Screws:** [Amazon](https://link.amazon/B0bxAbFGc) / [AliExpress](https://s.click.aliexpress.com/e/_c4doiwNR) *  
- **M3 Heat-Set Inserts:** [Amazon](https://link.amazon/B09prGJJ3) / [AliExpress](https://s.click.aliexpress.com/e/_c4Fz7ZI9) *  
___
## Support me!
You like the content and want to support me? [Buy me some ABS!](https://ko-fi.com/andystechlab)  
Or buy something with my [affiliate links](https://andystechlab.dev/product-links/) with no exra cost!  

**Some of the stuff i use:**\
PLA Filament: [Amazon](https://amzn.to/3Vauu4n) *  
ABS Filament: [Amazon](https://amzn.to/4lzb316) *  
Filament Dryer: [Amazon](https://amzn.to/42NVXxg) *  

*This link is an affiliate link, which means I may earn a commission at no extra cost to you.

---
title: "SolidCraft: Testing a Free, Open-Source Fusion Alternative"
date: 2026-10-21
publishDate: 2026-10-21T18:30:00+02:00
draft: false
showAuthor: false
showReadingTime: false
showWordCount: false
toc: true
tags:
  - CAD
  - opensource
image: featured.webp

---
{{< youtube id="INEZZ72nCBg" label="SolidCraft: Testing a Free, Open-Source Fusion Alternative" >}}

## Overview
Autodesk Fusion is a popular choice for designing parts for 3D printing. It offers a powerful parametric modelling workflow, but depending on how you use it, the subscription cost can be difficult to justify.

The free personal-use version is still an option for eligible non-commercial users, although it comes with some limitations.

That made me curious about SolidCraft, a free and open-source CAD application that takes a similar approach to parametric modelling.

I wanted to see how far I could get with a simple design, whether changing dimensions would work as expected, and how easily I could move the finished model into my 3D printing slicer.
___
## What Is SolidCraft?

SolidCraft is an open-source parametric 3D CAD application built in Rust. It offers a familiar workflow if you've used Fusion or other history-based CAD programs before.

You start with a sketch, define dimensions and constraints, and create solid features using operations such as extrusions. The modelling history is stored in a timeline, allowing you to return to earlier steps and make changes without starting from scratch.

One particularly interesting aspect is its platform support. SolidCraft runs on Windows, macOS, and Linux, and there's also a browser-based version.

Native Linux support is especially welcome. While there are already CAD options available for Linux, having another parametric modelling application to choose from is never a bad thing.

SolidCraft is still under active development, so it's important to approach it with realistic expectations.
___
## SolidCraft vs. Fusion Pricing

Cost is one of the obvious reasons to look into alternatives.

At the time I recorded the video, Autodesk listed a standard Fusion subscription at $85 per month or $680 per year when billed annually in the US. Prices may differ depending on your region or available promotions.

Fusion also has a free personal-use license for eligible non-commercial projects. If that version already does everything you need, there's no immediate financial reason to switch.

SolidCraft, on the other hand, is free and open source, without a subscription requirement.

Of course, there's more to choosing CAD software than its price. The important question is whether the tools you need are available and work reliably.
___
## Testing the Modelling Workflow

Rather than starting with a complicated project, I decided to test a few basic modelling operations.

I created a rectangular sketch and extruded it to form a simple solid part. After that, I added two circles and extruded them down through the material to create holes.

It's a straightforward example, but these are exactly the kinds of operations I regularly need when designing functional parts for 3D printing.

A CAD application doesn't have to handle an extremely complicated assembly to be useful. For many small workshop projects, brackets, mounting plates, adapters, and simple enclosures are the things that matter.
___
### Editing the Original Sketch

The more interesting part came after creating the model.

Instead of leaving everything as it was, I went back to the original sketch and changed its dimensions.

This is one of the main reasons I prefer parametric CAD for functional parts. You can start with an initial design, measure the actual space available, and adjust dimensions later.

SolidCraft rebuilt the model after I changed the sketch, demonstrating that the basic parametric workflow works for this example.

That doesn't mean every possible modelling operation or dependency will behave perfectly, but it's an encouraging result for everyday designs.
___
## From CAD to the Slicer

Once the model was finished, I wanted to see how easily I could prepare it for 3D printing.

SolidCraft includes a "Send to slicer" option as part of its mesh export workflow.

With the slicer configured, I could transfer the model directly into the slicing software instead of manually importing an exported file.

From there, the usual steps apply: check the model, choose the print orientation, slice it, and inspect the layer preview.

It's a small convenience, but I appreciate anything that makes the process from CAD to 3D printing a little smoother.
___
## Is SolidCraft Ready to Replace Fusion?

That depends on what you're doing.

For basic parts, SolidCraft already provides several of the tools I would expect from a parametric CAD application. Creating sketches, extruding geometry, adding holes, and changing dimensions are all important parts of my usual workflow.

The test in the video covers those basic operations, and the results are promising.

But Fusion is a much more established application with a broader set of tools and workflows.

Complex assemblies, specialised modelling features, CAM, simulation, and other advanced requirements are a different story. I haven't tested SolidCraft thoroughly enough in those areas to recommend it as a complete replacement.

There's also the question of long-term development.

According to the project's contribution documentation, AI coding agents have played a significant role in writing the software, with human direction and bug reporting. That's an interesting aspect of the project, but it doesn't automatically tell us how reliable the software will be.

What matters over time is how well bugs are fixed, whether the software continues to improve, and whether an active developer community can support it.

Open source makes it possible for others to contribute, but maintaining a CAD application still requires considerable work.
___
## My Thoughts

I wouldn't uninstall Fusion just yet.

Still, I think SolidCraft is an interesting project, particularly for Linux users and people who mainly design relatively simple parts for 3D printing.

The workflow feels familiar, the parametric editing is useful, and being able to send a model directly to the slicer is a nice addition.

It's not a complete replacement for every Fusion workflow, at least not based on what I've tested.

But if your CAD projects mostly involve sketches, extrusions, holes, and dimensional changes, SolidCraft is worth a look.

And since it's free, there's very little stopping you from giving it a try.
___
## Sources

- **Official Website:** [https://solidcraft.io/](https://solidcraft.io/)  
- **GitHub Repository:** [https://github.com/tangency-labs/solidcraft](https://github.com/tangency-labs/solidcraft)  
- **Documentation:** [https://docs.solidcraft.io/](https://docs.solidcraft.io/)  

___
## Support me!
You like the content and want to support me? [Buy me some ABS!](https://ko-fi.com/andystechlab)  
Or buy something with my [affiliate links](https://andystechlab.dev/product-links/) with no exra cost!  

**Some of the stuff i use:**\
PLA Filament: [Amazon](https://amzn.to/3Vauu4n) *  
ABS Filament: [Amazon](https://amzn.to/4lzb316) *  
Filament Dryer: [Amazon](https://amzn.to/42NVXxg) *  

*This link is an affiliate link, which means I may earn a commission at no extra cost to you.

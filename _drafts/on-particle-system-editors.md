---
layout: post
title:  "On Particle System Editors"
date:   2018-01-08 19:38:06 -0500
categories: blog
tag: post
published: false
---
One day at work, my neighbouring graphics programmer casually rolled over and asked _"So we're thinking of redoing the effects editor, do you have any thoughts on how it should work?"_. The short and simple answer would of course have been to just state what's missing and what could be improved, but instead I started thinking about the nature of effects editors, and why they look and work the way they do. I have a lot of thoughts, so be prepared for some verbosity.

For the sake of simplicity - let's divide up current major approaches into some categories:

### Spreadsheet Editors

Spreadsheet editors are what we're given in most tools currently. Unity, Unreal, Frostbite, and who knows how many other engines have all opted to give us an interface where you're presented with a number of fields where you can type in numbers, and thus author your effects. Some of these editors allow for advanced features such as supporting expressions or animated values, but in terms of interaction they are all largely the same.

### Node Editors

While still a relatively rare sight in realtime applications, node editors are definitely on the rise. They have a storied and proud heritage in offline applications such as 3ds Max, Softimage, and Houdini. The mythical beast [Niagara][niagara] has certain node-based components, but I'll withhold judgement until it's been properly released. Frostbite also implements a graph-based system for authoring GPU particle systems.

### Script Editors

Script Editors refer to systems such as [PopcornFX][popcornfx] or what was used in [Infamous: Second Son][infamous] where particle behavior is primarily driven through scripts and expressions. This approach is powerful and flexible, and lends itself well to people comfortable with programming. This flexibility offers immense creative freedom, with the caveat of making it just as easy to break the entire thing. But for all the freedom and power they offer, I would consider these editors the weakest in terms of intuitivity and artist-friendliness.

## The Problem

My issue with the above approaches all stem from a shared understanding of the nature of effects work. While they differ in terms of iterability and intuitivity, _they all stem from an assumption that effects work is a technical undertaking_. Let's imagine a world where that isn't the case; where effects authoring is closer to 3D sculpting or character animation rather than programming. Some ideas of what we'd potentially see:

### Larger emphasis on manipulators

The above approaches all have a focus on text entry, but rather than typing coordinates and dimensions for emission volumes, why not just place and scale them using the same manipulation tools we use for other 3d models? Speed and direction could be represented as arrows or vector fields, and adjusted directly. Trajectories could be drawn directly in the viewport as splines without the hassle of modulating XYZ velocities over life.

### Effects are defined as physical interactions

Particle systems in general treat particles as points in space with sizes and velocities. Fire is not defined by its heat, and rock is not defined by its mass.

---

It's of course easy for me to be wishful when I'm not in charge of the implementation, but I believe its an important exercise to second-guess the nature of the tools we use on a daily basis. I would like for VFX artists and engineers to spend some time reevaluating our assumptions regarding effects authoring, because _the notion that VFX authoring is a technical exercise rather than an artistic one is informing the way our tools are being designed._ The prevalence of the spreadsheet approach is is typical and disheartening example, since it demonstrates a lack of imagination in terms of how we see artists authoring effects.

I can't wait to see new paradigms for effects authoring be invented, and what we'll be able to make by that time.

My reasoning here is that it's the only approach that is _moving away from the idea that VFX work must be technical_. As far as game art goes, currently VFX is absolutely one of the more technical disciplines. It doesn't have to be that way though, but still  I believe we should try to move away from this mindset, and the first step is to decouple the editor interface from implementation. I believe we can change the way we work with effects systems without having to change a single line of backend code - it is just our interaction with the systems that need rethinking.

[niagara]: https://www.youtube.com/watch?v=BxpBJ8yAinE
[popcornfx]: https://www.popcornfx.com/
[infamous]: https://www.youtube.com/watch?v=o2yFxPY2b1o
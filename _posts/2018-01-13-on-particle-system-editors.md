---
layout: post
title:  "On Particle System Editors"
date:   2018-01-13 13:38:06 -0500
categories: blog
tag: post
published: true
---
One day at work, my neighbouring graphics programmer casually rolled over and asked _"So we're thinking of redoing the effects editor, do you have any thoughts on how it should work?"_. The short and simple answer would of course have been to just state what's missing and what could be improved, but instead I started thinking about the nature of effects editors, and why they look and work the way they do. I have a lot of thoughts, so be prepared for some verbosity.

As far as game art goes, effects work is absolutely one of the more technical disciplines. It strikes a razor-thin balance between classic art theory concepts such as color and composition, a sense of timing and impact often perfected by full-time animators, and lastly, a great deal of technical know-how.

Modern effects editors, in my mind, tend to focus less on the compositional, artistic, or animated process of effects authoring - instead making it a process focused on tweaking numbers. Let me make my case by quickly summarizing the major approaches we have to effects authoring:

### Spreadsheet Editors

Spreadsheet editors are what we're given in most tools currently. Unity, Unreal, Frostbite, and who knows how many other engines have all opted to give us an interface where you're presented with a number of fields where you can type in numbers, and thus author your effects. Some of these editors allow for advanced features such as supporting expressions or animating values over time, some of them provide a preview that updates in realtime while others require resaving and rebuilding after each change, but in terms of interaction they are all largely the same.

### Node Editors

While still a relatively rare sight in realtime applications, node editors are definitely on the rise. They have a storied and proud heritage in offline applications such as 3ds Max, Softimage, and Houdini. The mythical beast [Niagara][niagara] has certain node-based components, but I'll withhold judgement until it's been properly released. Frostbite also implements a graph-based system for authoring GPU particle systems. As with shader graphs, they are doing a strong effort of making the authoring of effects less text-based and more interaction-based, but the concepts and vocabulary is generally identical. 

### Script Editors

Script Editors refer to systems such as [PopcornFX][popcornfx] or what was used in [Infamous: Second Son][infamous] where particle behavior is primarily driven through scripts and expressions. This approach is powerful and flexible, and lends itself well to people comfortable with programming. But for all the freedom and power they offer, I would consider these editors the weakest in terms of intuitivity and artist-friendliness.

## The Problem

My issue with the above approaches all the assumptions from which their foundation is built. While they differ in terms of iterability and intuitiveness, _they all originate from an assumption that effects work is a technical undertaking_. It's not simply a matter of making tools more "artist friendly" (whatever that means), it's a matter of changing our vocabulary to something less abstract and mathematical. Let's imagine a world where effects authoring is closer to 3D sculpting or character animation rather than programming. Some ideas of what we'd potentially see:

* The above approaches all have a focus on text entry, but rather than typing coordinates and dimensions for emission volumes, why not just place and scale them using the same manipulation tools we use for other 3d models? Speed and direction could be represented as arrows or vector fields, and adjusted directly _(similar to what we see in [Impromptu Vector Field Painter](vectorpainter))_. Trajectories could be drawn directly in the viewport as splines without the hassle of modulating XYZ velocities over life.

* Particle systems treat its content as points in space with sizes and velocities, no matter what they're trying to mimic. Fire is not defined by its heat, and rock is not defined by its mass. This creates a dissonance when we at the same time insist on defining a constant downward force as _gravity_ or define wind speeds in physical units such as _m/s_. There is a discussion to be had in regards to how we can define and achieve physically correct visual effects in games, but that would easily warrant its own dedicated post.

The above examples illustrate what happens when we approach effects work as something _tangible_. When we describe particle systems by what we're trying to create rather than describing them as point positions and spawn properties. Not only would these systems be more approachable by artists with non-technical backgrounds, we would achieve a workflow that is more iterable, more art directable, and most importantly, more stimulating to work with.

It's of course easy to be opinionated when I'm not in charge of the implementation, but I maintain that it's an important exercise to second-guess the nature of the tools we use on a daily basis. I would like for effects artists and engineers to spend some time reevaluating our assumptions regarding effects authoring, because _the notion that effects authoring is a technical exercise rather than an artistic one is informing the way our tools are being designed._ The prevalence of the spreadsheet approach is is typical and disheartening example, since it demonstrates a lack of imagination in terms of how we see artists authoring effects. I believe we can change the way we work with effects systems without having to change a single line of backend code - it is just our interaction with the systems that need rethinking.

I can't wait to see new paradigms for effects authoring be invented, and discover what we'll be able to create at that time.

[niagara]: https://www.youtube.com/watch?v=BxpBJ8yAinE
[popcornfx]: https://www.popcornfx.com/
[infamous]: https://www.youtube.com/watch?v=o2yFxPY2b1o
[vectorpainter]: http://store.steampowered.com/app/684330/Impromptu_Vector_Field_Painter/
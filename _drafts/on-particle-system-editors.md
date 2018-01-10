---
layout: post
title:  "On Particle System Editors"
date:   2018-01-08 19:38:06 -0500
categories: blog
tag: post
---
One day at work, my neighbouring graphics programming casually rolled over and asked _"So we're thinking of redoing the effects editor, do you have any thoughts on how it should work?"_. The short and simple answer would of course have been to just state what's missing and what could be improved, but instead I started thinking about the nature of effects editors, and why they look and work the way they do. I have a lot of thoughts, so be prepared for some verbosity.

Let me just be clear, I _despise_ most effect and particle editors. More often than not they're spreadsheet simulators, with no intent of being approachable by artists.

For the sake of simplicity - let's divide up current major approaches into some categories:

## Spreadsheet Editors

Spreadsheet editors are what we're given in most tools currently. Unity, Unreal, Frostbite, and who knows how many other engines have all opted to give us an interface where you're presented with a number of fields where you can type in numbers, and thus author your effects.

## Node Editors

Node editors are definitely on the rise, and showing a lot of promise. While still a relatively rare sight in realtime applications, they have a storied and proud heritage in offline applications such as 3ds Max, Softimage, and Houdini. The mythical beast [Niagara](https://www.youtube.com/watch?v=BxpBJ8yAinE) has certain node-based components, but I'll withhold judgement until it's been properly released.

## Script Editors

By script editors I mean systems such as [PopcornFX](https://www.popcornfx.com/) where particle behavior is scripted rather than typed. While the capability of these editors range from incredible to incredulous, they all lack in how approachable they are for someone with a purely artistic background.
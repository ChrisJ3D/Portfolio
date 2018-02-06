---
layout: post
title:  "Houdini Quick Trick: Rendering Odd Frames"
date:   2018-02-06 18:54:06 -0500
categories: blog
tag: post
published: published
---
I've been dealing a lot with authoring flipbooks in Houdini lately, and I wanted to share a quick tidbit on rendering (and reading) image sequences that aren't very sequential.

Most output nodes in Houdini will allow you to output every nth frame, which saves both rendering time and disk space. However, the issue with this is that if you're using the default `$F` variable in your file names, you'll end up with files names such as 01, 03, 05, 07, etc. This makes things messy when you try to read these files back into Houdini for rendering or compositing purposes, or even if you're just trying to check things out in mplay. There are of course expressions to only read back every other frame, as well as external tools to batch rename files, but I wanted to show you a way to have them written correctly from the get-go.

Let's say that you're rendering out every 2 frames of `texture.$F4.tga`, but you want it to output 01,02,03.. instead of 01,03,05.. We can achieve this by replacing the filename with the following:

```texture.`padzero(4, floor($F/2) + 1)`.tga```

Let's deconstruct this expression:

* `padzero()` is function that adds padding to a number, which allows us to emulate the 4 in `$F4`. The first argument is how many digits to pad with, while the second argument is the number to pad. `padzero(2, 5)` evaluates to `05`, `padzero(6, 24)` evaluates to `000024`, etc.
* `floor()` is a common math function to round a number downwards. Since frame numbers should be integers (whole numbers), we use `floor()` to round results such as `64.3` down to `64`.
* `$F/2`, as you might guess, simply divides the frame number by 2. If you are outputting every third, seventh, etc. frame instead, you should replace 2 with the desired number.

So in practice, what happens when we're rendering out frame 37 of our simulation is the following:

* `$F/2` will divide 37 by 2, outputting 18.5
* `floor(18.5)` will round it down to 18
* `18 + 1` is something we need since frame 1 evaluates to 0
* `padzero(4, 19)` will pad the number, outputting 0019

Using some expression magic, we should now have beautiful filenames that behave predictably when used with other programs!

### Bonus Lesson: Linking to the Increment Parameter

Let's say that you find yourself experimenting with different increments, but you don't want to update the `$F/2` part of the expression constantly to match what you've entered. On most ROP output nodes, the increment parameter is referred to as `f3`, so by instead writing `$F/ch('f3')` it'll reference whatever assigned to the Increment parameter. _Proceduralism!_

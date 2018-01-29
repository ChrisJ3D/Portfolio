---
layout: post
title:  "Houdini Quick Trick: Bounds-seeking Camera"
date:   2018-01-23 18:54:06 -0500
categories: blog
tag: post
published: false
---
Work continues to be insane this week, but in the midst of everything I came up with a neat little trick that I wanted to share: The idea is to create a camera that adjusts itself to keep the subject matter in roughly the same texture space throughout the animation.

This is a useful technique especially for those authoring flipbook texture sheets, where each frame ideally fills up as much texture space as possible. While this can be done manually by cropping the render frames, Houdini allows us to easily automate the process.

1. Create an orthographic camera and place it facing directly down at your target
2. Open up the _Edit Parameter Interface_ window and add two new channels: an operator path and a float
3. Set the operator path name to _targetPath_ and the float name to _ortho\_padding_. For kicks we can set the default value of _ortho\_padding_ to 1
3. Enter the following expression in the _Ortho Width_ channel:
    ```max(node(hou.evalParm("targetPath")).geometry().boundingBox().sizevec()[0], node(hou.evalParm("targetPath")).geometry().boundingBox().sizevec()[2]) + hou.evalParm("ortho_padding")```
    _Note: This expression assumes a downward-facing camera, and only tracks the X and Z extents of the bounding box. If you need to track the height of the bounding box, change one of the sizevec() elements to [1]._
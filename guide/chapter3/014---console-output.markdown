---
title: Console output
permalink: "console-output.html"
layout: default
section: 2
indent: 2
---

Console output is what you will be looking at when developing tweaks. The might be a way to use a debugger but that's nothing I've used so I will stick to `NSLog`.

Plug your device into your computer with USB. Open `Xcode`, click `Windows` in the menu and choose the `Organizer`. Your device should show up on the left side and you should also see an option named "console". Click this and you should see a giant wall of text. This is your devices "syslog" and this is where lots of things get logged, including anything that is "`NSLog`ged".

![assd](/guide/img/9.png "asd")

Keep this in mind, as this is where you will be looking at some point or another.
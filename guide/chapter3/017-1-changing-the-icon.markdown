---
title: Changing the icon
permalink: "changing-the-icon.html"
layout: default
section: 2
indent: 2
---

As you've noticed there is no icon for the entry on the settings panel. This is easy to change. The file `entry.plist` (inside the `/sliderchangerprefs/` directory) contains an entry called `icon = SliderChangerPrefs.png`.

Now go to the folder `/sliderchangerprefs/resources/` and put a `58x58` file here, and name it `SliderChangerPrefs@2x.png`. For non-retina devices you should also put a `29x29` file here with the same name, removing the `@2x` part.
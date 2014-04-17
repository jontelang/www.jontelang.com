---
title: The research
permalink: "the-research.html"
layout: default
section: 2
indent: 1
---

I'd love for you to just be able to get into the coding and do the tweak instantly. But do you even know where to begin? Probably not. The next step is to dig into your headers, get used to it because you will spend an increbible amount of time reading them. It gets easier after a while.

With this project though, I will give you some hints. We are looking for the lockscreen-slider-bar-text right. So firstly we look for the lockscreen. I happen to know that the lockscreen is called `SBLockScreenView`. So open this up and look/search for something that could have to do with the 'slide to unlock' text. There seems to be a method called `-(void)setCustomSlideToUnlockText:(id)arg1` that could be interesting. This method is pretty well-named, and we are fairly sure that this is the actual code we are looking for. 

In fact, it IS the code we are looking for so I will just continue with the tutorial instead and you will understand how to "console-log-research" other classes in the future. This next line may not make 100% practical sense now, but it will later. To "console-log-research" you will later just `%hook` a bunch of correctly-sounding classes, hijack their methods and log them to find the things you want.
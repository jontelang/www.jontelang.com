---
title: The code
permalink: "the-code.html"
layout: default
section: 2
indent: 1
---

Time to write some actual code.

Open `Tweak.xm` and remove all pre-written text. We will be working the class from the "The research" chapter called `SBAwayLockBar` and its method `setLabel`. 

In your `Tweak.xm` write the following.

{% highlight objective-c %}
%hook SBAwayLockBar
-(void)setLabel:(id)arg1
{
	arg1 = @"SliderChanger";
	%orig(arg1);
}
%end
{% endhighlight %}

This is pretty straight forward. You are "hooking" into the class `SBAwayLockBar` and hijacking the method `setLabel`. The argument `arg1` may say `id` but in reality it is an `NSString`. So we reset the argument to `@"SliderChanger"` and then we call the original method with the updated argument. We do this by calling `%orig(arg1)`.

We then close the `%hook` with `%end`.

Now go to the terminal again and write `make package install` to install the new tweak to your device. By now it should have changed the "slide to unlock" to "SliderChanger".

![test](/guide/img/1.png "1")

Congratulations, you are now an iOS tweak developer.
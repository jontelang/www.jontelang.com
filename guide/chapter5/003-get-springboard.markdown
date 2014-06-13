---
title: Get the SpringBoard object
permalink: "get-springboard-object.html"
layout: default
section: 4
indent: 1
---

Sometimes you want to use the methods within the `Springboard` so here is a way to do just that! It is really simple and it is basically just an `UIApplication`. For example if you want to respring there is (since iOS6 or 7 I believe) a method for just that.

{% highlight objective-c %}
SpringBoard *springboard = (SpringBoard*)[NSClassFromString(@"SpringBoard") sharedApplication];
[springboard relaunchSpringBoard];
{% endhighlight %}

And if you get a compile error you might want to declare its interface before doing that.

{% highlight objective-c %}
@interface SpringBoard : UIApplication
-(void)relaunchSpringBoard; // Respring
@end
{% endhighlight %}

And that's it.

Instead of using `NCClassFromString("SpringBoard")` you can use `objc_getClass("SpringBoard")` or with theos `%c(SpringBoard)`. I actually think the last one it preferred while using theos, but any one works.
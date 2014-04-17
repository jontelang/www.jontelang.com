---
title: Accessing saved settings
permalink: "accessing-settings.html"
layout: default
section: 2
indent: 2
---

Your settings area is now completed, it will save the settings to a file in the directory (see above) and it is now time for your tweak to read it. And with the `PostNotification` it will also be able to reload it instantly without the need for a respring.

Open up your `Tweak.xm` and change it to this.


{% highlight objective-c %}
static BOOL SCisEnabled = YES; // Default value
static NSString* SCtext = nil;

%hook SBLockScreenView
- (void)setCustomSlideToUnlockText:(id)arg1
{
	if(SCtext && SCisEnabled)
	{
		arg1 = SCtext;
	}
	%orig(arg1);
}
%end

static void loadPrefs()
{
    NSMutableDictionary *prefs = [[NSMutableDictionary alloc] initWithContentsOfFile:@"/var/mobile/Library/Preferences/com.jontelang.sliderchangerprefs.plist"];
    if(prefs)
    {
    	SCisEnabled = ( [prefs objectForKey:@"SCisEnabled"] ? [[prefs objectForKey:@"SCisEnabled"] boolValue] : SCisEnabled );
    	SCtext = ( [prefs objectForKey:@"SCtext"] ? [prefs objectForKey:@"SCtext"] : SCtext );
    	[SCtext retain];
    }
    [prefs release];
}

%ctor 
{
    CFNotificationCenterAddObserver(CFNotificationCenterGetDarwinNotifyCenter(), NULL, (CFNotificationCallback)loadPrefs, CFSTR("com.jontelang.sliderchangerprefs/settingschanged"), NULL, CFNotificationSuspensionBehaviorCoalesce);
    loadPrefs();
}
{% endhighlight %}
	
The `%ctor` thing here is a method which will run when the tweak is loaded, it will only run once (per respring) and is the place we use to register the tweak for listening to our `PostNotification`. The register method specifies which string to listen to and which method to call when it gets the correct string. I've created a method called "loadPrefs" that is run each time. This method simply loads the settings-saved file and reads the values from it. 

> TIP: Remember to (as in my case) make sure the value is actually present in the dictionary/file. Otherwise you might end up with mismatched default values and so on.

The rest of the tweak is pretty straight forward. I just create some static variables and add the extra check in `setCustomSlideToUnlockText` to make sure nothing is modified if the tweak is, for example, disabled.
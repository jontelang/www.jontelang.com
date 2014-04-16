---
title: Changing the settings
permalink: "changing-the-settings.html"
layout: default
section: 2
indent: 2
---

Now you'd go into the newly created folder (in your tweaks folder) and you should see another folder called "resources". Open this and find a `.plist` file with the contents. 

The file will contain the following (or similar, at least):

{% highlight xml %}<plist version="1.0">
<dict>
	<key>items</key>
	<array>
		<dict>
			<key>cell</key>
			<string>PSGroupCell</string>
			<key>label</key>
			<string>test First Page</string>
		</dict>
		<dict>
			<key>cell</key>
			<string>PSSwitchCell</string>
			<key>default</key>
			<true/>
			<key>defaults</key>
			<string>test</string>
			<key>key</key>
			<string>AwesomeSwitch1</string>
			<key>label</key>
			<string>Awesome Switch 1</string>
		</dict>
	</array>
	<key>title</key>
	<string>test</string>
</dict>
</plist>
{% endhighlight %}

You can change it so that it looks like this (using your own name instead of my "jontelang").

{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>items</key>
	<array>
		<dict>
			<key>cell</key>             <string>PSGroupCell</string>
		</dict>
		<dict>
			<key>cell</key>             <string>PSSwitchCell</string>
			<key>default</key>          <true/>
			<key>defaults</key>         <string>com.jontelang.sliderchangerprefs</string>
			<key>key</key>              <string>SCisEnabled</string>
			<key>label</key>            <string>Enabled</string>
			<key>alternateColors</key>  <true/>
			<key>PostNotification</key> <string>com.jontelang.sliderchangerprefs/settingschanged</string>
		</dict>

		<dict>
			<key>cell</key>             <string>PSEditTextCell</string>
			<key>defaults</key>         <string>com.jontelang.sliderchangerprefs</string>
			<key>key</key>              <string>SCtext</string>
			<key>label</key>            <string>Text</string>
			<key>PostNotification</key> <string>com.jontelang.sliderchangerprefs/settingschanged</string>
		</dict>
		<dict>
			<key>cell</key>             <string>PSButtonCell</string>
			<key>label</key>            <string>Save</string>
			<key>action</key>           <string>save</string>
		</dict>
	</array>
	<key>title</key>
	<string>SliderChanger</string>
</dict>
</plist>
{% endhighlight %}

This is the layout of the settings panel. If you read through them slowly they all make sense. The "defaults" key is basically the id-key-thing that the tweak will save to. All files will be located in `/var/mobile/Library/Preferences/com.yourtweak.yourtweakprefs.plist`. You'll be spending time in that folder (iFile) so make a shortcut to it.

One most notable thing here is the key `PostNotification` which is a way to avoid having to respring for your changes to take effect. This specifies a string which will be sent to the system, and your tweak will - at launch - register itself for this string. You'll see this code soon.

The button in the last panel have a `action` key which specifies a method to be run when it is clicked. The method you will add in your `SliderChangerPrefs.mm` looks like this (see below). What it does is that it de-focuses the keyboard for the `PSEditTextCell` and thus the content are saved (and the `PostNotification` is sent).

{% highlight objective-c %}
-(void)save
{
	[self.view endEditing:YES];
}
{% endhighlight %}

At this point, your settings panel should look something like this.

![asd](/guide/img/8.png "ads")
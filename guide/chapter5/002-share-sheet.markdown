---
title: Share-sheet from SpringBoard
permalink: "share-sheet-springboard.html"
layout: default
section: 4
indent: 1
---

While working on Snapper I was asked to include share options. These includes things like "share on facebook" and "copy image" actions. So here is how to do this.

The tweak named above creates a `UIWindow` where all action happens. And we want to open a `UIActivityViewController` where all sharing is then taken care of by iOS (6+). A `UIWindow` cannot, by itself, open a ViewController. It needs to be opened in another ViewController it seems. 

The solution is to simply create a `UIViewController` for the `UIWindow` and use that, the controller is then set as the rootViewController.

{% highlight objective-c %}
UIViewController *tempVC = [[UIViewController alloc] init];
self.rootViewController  = tempVC;

UIActivityViewController *activityController = 
		[[UIActivityViewController alloc] 
			initWithActivityItems:@[self.imageToShare] 
			applicationActivities:nil];

activityController.excludedActivityTypes = @[UIActivityTypePrint];

activityController.completionHandler = ^(NSString *activityType, BOOL completed){ 
    if( completed == YES ){
        // This means the sharing was completed
        // Pressing "cancel" on eg. the mail will set completed to 'NO'
    }else{
    	// Because I only use the UIViewController temporarily
    	// I decided to remove it here. It should probably not
    	// be done like this but hey, it works fine.
        self.rootViewController = Nil;
        [tempVC release];
        [activityController release];
    }
};

// Show it
[tempVC presentViewController:activityController animated:YES completion:Nil];
{% endhighlight %}

If someone knows a way to present the share controller directly from SpringBoards rootViewController feel free to send me an email, because I could not get this to work.
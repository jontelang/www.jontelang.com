---
title: Resetting the version
permalink: "resetting-the-version.html"
layout: default
section: 2
indent: 2
---

You might have noticed that your tweaks version increases its build number each time you do `make package`. When you release it you might not want to have the version as 0.0.1-2526. Maybe you want to have it as 1.0 or similar. 

To change this you simply open the file `control` and change the version to whatever you want.

Note that this will still not get rid of the build number, so if you set it to 1.0 the actual version will be 1.0-1. For your next version you may want to have it as 1.0-2, but the actualy version might be 1.0-65 at the point of release. To reset the counter to 0 you will go to an invisible folder called `.theos` which lies in the tweaks project root folder. Inside this there will be another folder called `packages`. Open this folder and delete the files inside it. Next time you build you will have the version at 1.0-1 again.

> NOTE: These versions might not even matter (at least when submitting to the BigBoss repo) as the repos de-assemble and re-assemble the packages when they get them. Also, when submitting to the BigBoss repo you can enter the version number. For more info though, ask the repo managers.
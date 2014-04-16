---
title: The project
permalink: "the-project.html"
layout: default
section: 2
indent: 1
---

Start by going to your terminal and create a new theos project with the `/opt/theos/bin/nic.pl` command. Choose the tweak option and follow the wizard. 

![asd](/guide/img/3.png "asd")

> TIP: To avoid having to rewrite the "com.yourcompany" part each time you make a new tweak you can open the actual "nic.pl" file, search for "com.yourcompany" and replace it with your preffered name. In my case I changed it to "com.jontelang".

Name the tweak "SliderChanger". In my case it became "com.jontelang.sliderchanger".

After you have finished you should end up with a directoy like this.

![asd](/guide/img/2.png "asd")

Run `make package install` and make sure the tweak is listed under S in the cydia installed packages section.
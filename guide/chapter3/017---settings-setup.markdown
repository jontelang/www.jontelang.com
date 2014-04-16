---
title: Subproject setup
permalink: "settings-setup.html"
layout: default
section: 2
indent: 2
---

`cd` into your tweak folder and start the theos-templates-menu with `/opt/theos/bin/nic.pl`. Choose the `preferencebundle` option and follow the wizard. I prefer to use my tweaks name here with the additional "prefs" at the end. In my case it becomes "com.jontelang.sliderchangerprefs".

![asd](/guide/img/5.png "asd")

Once done your tweak folder should now look like this, with an extra folder inside it. 

![asd](/guide/img/6.png "asd")

There have been some changes inside the `makefile` also which you can look at, although it is not very important at the moment.

By now you should be able to just `make package install` to verify that there is an additional entry with your tweaks name. 

It should look something like this.

![asd](/guide/img/7.png "asd")


#### Changing the text/icon/etc

Blabla
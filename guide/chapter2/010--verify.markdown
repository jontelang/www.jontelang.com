---
title: Verify that everything works
permalink: "verify.html"
layout: default
section: 1
indent: 1
---

First, open the terminal and `cd` to your `~/Desktop/`. Write the command `/opt/theos/bin/nic.pl/` and choose the "tweak" option, finish the wizard and `cd` into the directory and write `make`. This will show you whether the compilation (etc) worked or not. Hopefully it worked fine.

Write `export THEOS_DEVICE_IP=XX` where `XX` is the actual IP of your iOS device.

Now run the command `make package install` and enter your devices password (default is `alpine`). Your device should respring and this should mean that the tweak has successfully been transferred to your device. You can verify by looking in Cydia's installed packages.
## HOW TO DEBUG AN APP OVER WIFI (WITHOUT PHYSICAL USB CONNECTION TO THE DEVICE):

I found this trick long ago, when I bought a cheap no-named Android tablet that my computer never identified correctly. The device was OK, not wonderful, but it did the job for a while.

When I tried for the first time connect it to my computer and start debugging apps on it, I found that my computer never picked it correctly. Using standar usb drivers I could connect to it and use it almost as any other device, but Android ADB never understood it propertly and I couldn't debug any app on it using USB cables.

However, there is a way to connect to the device withouth using USB, the only thing you really need is have the Android device and your computer connected to the same network and then make some magic typing some commands on both of them. Here they are:

On your Android device, open a terminal (maybe you will need to be root) and type these commands:
```bash
setprop service.adb.tcp.port 5555
stop adbd
start adbd
```
5555 is a random port at your choice, but remember that the port you chose has to be free. By default, usually, on your computer the usb debug port for ADB is 5554, for that reason I didn't go too far away...

Now, on your coumputer, run your favourite command line terminal and type this:
```bash
adb connect <tablet_ip_here>:5555
```
ADB should be on your PATH, environment vars or whatever you like to name it. Usually is if you installed Android SDK by their installer.

And that's it! Easy-peasy, isn't?
Now the device should be connected and you should see it in the ADB connected devices list.

It does the job perfectly well, in the same way (AFAIK... I've never found any limitation using this way...) that connecting physically the device and the computer using an actual usb cable.

I hope this helps you if you are facing the same issue.
Enjoy!


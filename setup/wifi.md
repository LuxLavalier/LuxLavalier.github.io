---
layout: page
title: Wi-Fi Setup Instructions
---

Your Lux Lavalier should automatically play a playlist of pre-selected patterns endlessly (well, until the battery runs out and needs recharged).

For more control, you can connect to it via wi-fi.

**Note:** Wi-fi is disabled, by default, to conserve battery power.

---

##### To turn on wi-fi:

1. Ensure your Lux Lavalier is powered on with a freshly charged battery.
1. Press and hold the button on the back for 5 seconds. The status LED on the back will flash twice.
1. Wi-fi is now enabled until power is disconnected.

---

##### To connect your Lux Lavalier to a wi-fi network:

1. If not already connected to a wi-fi network, your Lux Lavalier will create its own network named Pixelblaze_XXXXXXX,
   where XXXXX is a code unique to your Lux Lavalier. You should see it in the list of wi-fi networks available on
   a computer or mobile device:

   <img src="/assets/img/setup/wifi-android.png" class="img-thumbnail" style="width: 240px" />

   **Note:** If you can't find the Lux Lavalier's wi-fi network, it may not be in setup mode.
   
   To put it in to setup mode:
   1. Press and hold the button for 5 more seconds.
   1. If the status LED on the back flashes 5 times, it's now in setup mode.
   1. If the status LED on the back flashes once, press and hold the button for 5 more seconds.
   The status LED on the back should now flash 5 times, 
   1. It should now be in setup mode and its wi-fi network should now appear in the list on your computer or mobile device.

1. Connect to this network from a computer or mobile device.
1. You should see a pop-up and/or automatically get redirected to configure the Lux Lavalier's wi-fi settings.
   If not, open a browser and go to [http://192.168.4.1](http://192.168.4.1)

   <img src="/assets/img/setup/wifi-settings.jpeg" class="img-thumbnail" style="width: 240px" />

In WiFi Settings you an configure your Lux Lavalier to run in one of two modes:

##### Client Mode - Connect to a network

---

In this mode your Lux Lavalier can connect to an existing wi-fi network.
Use this mode while at home or another location with an existing wi-fi network that you can connect to.

1. Choose the wi-fi network to which you'd like to connect, or enter the SSID (Name) if you know it, it's hidden, etc.

   <img src="/assets/img/setup/wifi-settings-2.jpeg" class="img-thumbnail" style="width: 240px" />

1. Enter the password for the wi-fi network.
1. Leave **Enable Discovery Service** enabled to use the [Pixelblaze Discovery Service](http://discover.electromage.com),
   which makes it much easier to find your Pixelblaze on your wi-fi network later.
1. Click Submit to connect.

   <img src="/assets/img/setup/wifi-settings-3.jpeg" class="img-thumbnail" style="width: 240px" />

1. Once it has connected, it will have an IP address on your wi-fi network.
1. The computer or mobile device you're using should automatically re-connect to its previous network (your home wi-fi, mobile data, etc).
1. If you left it enabled, use the [Pixelblaze Discovery Service](http://discover.electromage.com) to find your Lux Lavalier.
1. If you're unable to find your Lux Lavalier's IP address, you can use [these instructions for finding a Raspberry Pi](https://www.raspberrypi.org/documentation/remote-access/ip-address.md).

---

##### AP Mode - Create a stand-alone network

In this mode your Lux Lavalier will create its own wi-fi network that you can connect to from another device.
Use this mode when outdoors or away from other wi-fi networks.

If you've already chosen **Client Mode** and followed the instructions above, skip down to [**Next Steps**](#next-step-settingssetupsettings)

1. Enter an SSID (Name).
   This is the name of the wi-fi network that you will connect to from other devices to configure your Lux Lavalier.
1. Enter a password at least 8 characters long. Passwords with fewer than 8 characters will not work.
1. Now you should be able to use a computer or mobile device to connect to the wi-fi network with the SSID (name)
   you entered in step one above.
1. Once connected, open a browser and enter the address [http://192.168.4.1](http://192.168.4.1)

---

Congratulations! You should now be able to connect to and configure your Lux Lavalier!

##### Next step: [Settings](/setup/settings)

# 🌀 Web Portal

## What is web portal?
Web Portal is a web server application that serves up webpages when the IP address or hostname of the machine running the software is accessed via a web browser.

This provides a convenient way of accessing the device without the need for any of the following:
* spare mouse and/or keyboard
* a display

Instead, all you need is a device that can connect to your device via a web browser.
The additional benefit of this is that it does not require a dedicated VNC or SSH client to access the device.

## What is it currently used for?
Right now, it serves up webpages for user onboarding (OS setup, etc.).

## What will it do in the future?
As the application continues to mature, we intend to build all of our GUI interfaces as web apps that are served via the web portal backend. Applications on the desktop will open in a native-looking window that points to the local server to present the GUI and handle user interaction.

This includes the OS updater, which currently uses a terminal window - an approach that can cause unintended issues for users.

## How might this affect what I can do on pi-topOS?
The web portal requires TCP port 80. If you require port 80, then you will need to disable the web portal:

```sh
sudo systemctl disable pt-web-portal
```

> ⚠️ This will disable all of pi-top's own graphical applications that run on the desktop.

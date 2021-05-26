# Overview

pi-topOS is the recommended way to use your pi-top.

pi-topOS is built on top of Raspberry Pi OS (formerly Raspbian), so a lot of things are identical.
However there are some differences.

The underlying operating system (Raspberry Pi OS) handles much of the backbone functionality that pi-topOS depends on -
things like the desktop environment, software update management, etc.

> pi-topOS developers are not directly involved in the development of much of the low-level core features of pi-topOS.
> Rather, pi-topOS is 'downstream', and therefore directly benefits from this work done by the Raspberry Pi Foundation.
> 
> ⚠️ In rare circumstances, unexpected changes to Raspberry Pi OS can cause breaking changes to pi-topOS.
> Fortunately, this is a rare occurrence!

## So pi-topOS is built on top of Raspberry Pi OS. What's different?
pi-topOS extends upon Raspberry Pi OS to add additional functionality and usability improvements:

- Plug-and-Play functionality with pi-top hardware
- Modifying the user interface (including theming)
- Notification system
- Automatic software updater
- Simplified user onboarding/OS setup
- Additional settings for pi-top hardware
- ‘About’ page to show key information about the OS that is installed

> For more information about pi-topOS, check out the technical details subsection of the pi-topOS knowledge base

## What if I want to use Raspberry Pi OS?
Some users prefer to stick to Raspberry Pi OS and install the minimal device drivers to get Plug-and-Play
functionality with pi-top hardware without the additional customisations of pi-topOS.

If you'd like to use a pi-top device with Raspberry Pi OS, take a look at this article.

## What if I want to use another operating system?
> ⚠️ **Other operating systems are not supported.**

For a pi-top device to work properly, communication is required between the Raspberry Pi and the pi-top's onboard
"Hub" (microcontroller unit, or MCU).
At this time, the software for working with a pi-top is only available for Raspberry Pi OS-based systems.

Without this communication, all pi-top devices will be unable to power off correctly.
The power button will need to be held in place for longer to force a hard shutdown, which is dangerous and could cause
serious SD card corruption.
Shutting down the Raspberry Pi via a 'soft shutdown' (asking the operating system to shut down, such as via the start
menu) will turn off the Raspberry Pi, but the pi-top device will continue to be powered on.

Additionally, hardware will not work as intended - for instance, display brightness on pi-top laptops and the
miniscreen on the pi-top [4].
For pi-top devices with an onboard battery, it will not be possible to determine its state.

> If you are using an unsupported OS, it is recommended that you power off your Raspberry Pi via the start menu and wait
until the Raspberry Pi has halted before powering off the pi-top hardware via the hardware power button.

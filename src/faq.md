# 🙋 FAQs

## Why can't I update?
Check out our [knowledge base article](https://knowledgebase.pi-top.com/knowledge/error-updating-sirius) for guidance on updating issues.

## Why can't I connect to Further?
Check out our [knowledge base article](https://knowledgebase.pi-top.com/knowledge/why-cant-i-connect-to-further) for guidance on connecting to Further.

## Why can't I use port 80?
Check out our [knowledge base article](https://knowledgebase.pi-top.com/knowledge/pi-topos-port-80) for guidance on working with TCP port 80.

## Why does my screen resolution keep resetting on reboot?
`autorandr`, HDMI forced output, 

## How does pi-topOS handle versioning?
See the glossary for more information about the previous versions and their respective names.

pi-topOS is based on Raspberry Pi OS, which is based on Debian. Debian changes every \~18 months.

## Why is pi-topSPEAKER not mentioned/included in the pi-top Python SDK?

pi-topSPEAKERs are automatically configured and initialized via `pt-device-manager`. Because there are no desirable programmatic hardware settings, there is no exposed public API for this hardware.

## Why does my pi-top [4] require a modified EEPROM?

Raspberry Pi 4 boards earlier than the 1.4 PCB revision (All 8GB models have this, and this is now also the default for 2GB and 4GB models) require a modified EEPROM to power off correctly.

These newer boards hold the external reset until it is released by software (SPI bootloader) when the watchdog/soft reset occurs.

This means that the 5V rail on the USB bus will be off until the second stage bootloader has initialised or if halting it will stay off. On previous board revisions, this was not under software controls so 5V would be initialised when the XHCI/VLI automatically initialised, which could happen before halt.

Therefore, it is necessary to update the Raspberry Pi's internal EEPROM firmware to behave correctly. The following changes are made to the EEPROM:

```shell
WAKE_ON_GPIO=0
POWER_OFF_ON_HALT=1
```

> ⚠️ There is a very small risk of damage to Raspberry Pi HATs where 5V is powered but 3V3 is off (unless the HAT is designed to support that power configuration). Check with your HAT manufacturer to find out more.

## Is my hardware up to date? How can I check?

First, ensure that your OS is up to date. Then, connect any external peripherals you have. If you get a notification asking to update, then apply it. After this, you should have the latest version of the firmware (embedded software) for your pi-top hardware! Run `pi-top devices` in the terminal to check the firmware version of any applicable devices.

## Why is my pi-top v1 reporting itself to be a pi-topCEED?

[`pi-topd`](https://github.com/pi-top/pi-topd) uses the presence of the battery to identify a pi-top v1.
If this is not possible, then it will assume that it is now connected to a pi-topCEED.
The battery is detected by scanning for its I2C address (``0x0b``). You can see if the Raspberry Pi can 'see' the device by scanning for I2C addresses:

    sudo i2cdetect -y 1

If you cannot see `0b` in the list, then there is likely a hardware issue.

## What GPIO pins/I2C addresses/SPI busses do pi-top devices use?

| Device                     | I2C Address | SPI Bus
| -------------------------- |:-----------:|:-----------:|
| pi-topHUB v1 (pi-top)      |     0x0b    |      1      |
| pi-topHUB v1 (pi-topCEED)  |      -      |      1      |
| pi-topHUB v2               |     0x10    |      -      |

| Peripheral               | I2C Address |
| ------------------------ |:-----------:|
| pi-topPROTO+             |     0x2a    |
| pi-topPULSE              |     0x24    |
| pi-topSPEAKER v1 (Left)  |     0x71    |
| pi-topSPEAKER v1 (Right) |     0x72    |
| pi-topSPEAKER v1 (Mono)  |     0x73    |
| pi-topSPEAKER v2         |     0x43    |

# Troubleshooting

This section of the documentation aims to provide useful information to assist with identifying issues with pi-topOS.
Be sure to check out our FAQ section, that aims to address the most common questions/problems that people have.

## Collecting and Reviewing System Information

Find out how to collect useful information about your pi-top device's operating system and hardware state, and understand how to decipher/use it.


### Collecting System Information
On pi-topOS you can run the following command:

```bash
pi-top support health_check
```

This will generate some potentially useful information about the state of the device.

> ⚠️ **WARNING**: It is recommended that you review this data carefully before passing it to someone else - it may reveal personal information about your setup that you may not wish for others to know about.
>
> Do not give this information to anyone you do not trust without first checking its contents.

### Interpreting System Information
#### Raspberry Pi Device Information
Identifies the Raspberry Pi model type, and provides information about the state of the Raspberry Pi device, such as bootloader configuration, EEPROM version and GPU information.

#### pi-top Devices
Identifies what type of pi-top device the Raspberry Pi identifies that it is communicating with, and if any pi-top peripherals are connected or not.

#### System Information
Provides information about the active kernel, as well as pi-topOS build information.

#### Interfaces/Boot Settings/Misc (via raspi-config)
Shows information that can be determined via the 'raspi-config' tool.

#### Network Settings
Shows key network information, such as hostname, WiFi country, interfaces, IP addresses, etc.

#### pi-top Software Information
Shows the current state of pi-top software provided as systemd services, as well as the version of each pi-top software package.

#### pi-top Device Information
Provides hardware-level detail about the state of the pi-top hub.

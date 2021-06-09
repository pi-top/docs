# 💁 Tips & Tricks

This section seeks to offer useful tips for working with pi-topOS, although many of these tips are more broadly useful.

### Aliases

Aliases are a great way to shorten the amount you need to write in a terminal if you find yourself running the same commands over and over.

Read the [Raspberry Pi's documentation](https://www.raspberrypi.org/documentation/linux/usage/bashrc.md) for how to set this up.

Here are some potentially useful suggestions for you to get started with. Obviously, you can change the alias and the command that is called to suit your purposes.
However, take care not to accidentally use the same name as a command on your system, as it will require additional maintenance effort.

#### Faster printing to pi-top [4] miniscreen
This alias will display some text onto a pi-top [4] miniscreen for 10 seconds.

Alias Line:
```bash
alias pt-write="pitop oled write -t10"
```

Usage:
```bash
pt-write "Hello World"
```

### Changing Systemd Service Behaviour Using Environment Variables

This section documents specific use-cases where system behaviour can be modified by systemd environment variables.

#### How to update a systemd service's environment
Run the following in a terminal:
```bash
sudo systemctl edit <service>
```

Paste this into the editor and save:
```bash
[Service]
Environment="KEY=VAL"
```

Finally, reload systemd manager configuration and restart the service:
```bash
sudo systemctl daemon-reload
sudo systemctl restart <service>
```

#### Additional battery logging

Battery messages are no longer logged by default to reduce logging, which takes up unnecessary file system space. To enable this additional logging, set `PT_LOG_BATTERY_CHANGE=1` in the `pt-device-manager` systemd service.

```bash
sudo systemctl edit pt-device-manager
```

```bash
[Service]
Environment="PT_LOG_BATTERY_CHANGE=1"
```

```bash
sudo systemctl daemon-reload
sudo systemctl restart pt-device-manager
```

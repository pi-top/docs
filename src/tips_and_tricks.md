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

#### Controlling Systemd Services

Many parts of pi-topOS are managed by systemd services - for example, ``pi-topd`` runs as a systemd service which starts with the OS and stops on shutdown. However, for diagnostic or debugging purposes it can be useful to start and stop it, or to run it standalone.

For example, to check the current status of the `pi-topd` service:

<pre style="background-color: #002b36; color: #FFFFFF;">
sudo systemctl status pi-topd

<span style="color:#E0E0E0"><span style="color:#859900">●</span> pi-topd.service - pi-top device auto-detection and configuration daemon
     Loaded: loaded (/lib/systemd/system/pi-topd.service; enabled)
     Active: <span style="color:#859900">active (running)</span> since Tue 2017-10-17 15:55:43 UTC; 1s ago
 Main PID: 15974 (pt-device-manag)
     CGroup: /system.slice/pi-topd.service
                     └─15974 /usr/bin/python3 /usr/lib/pi-topd/pi-topd</span>
</pre>

Starting/stopping the service:

<pre style="background-color: #002b36; color: #FFFFFF;">
sudo systemctl start pi-topd
sudo systemctl stop pi-topd
</pre>

Stopping and disabling the service, and then running standalone:

<pre style="background-color: #002b36; color: #FFFFFF;">
sudo systemctl stop pi-topd
sudo systemctl disable pi-topd
pi-topd
</pre>

#### Viewing Systemd Service Logs

As the pi-topd runs as a systemd service, it logs to the system journal. This can be viewed using commands such as:

<pre style="background-color: #002b36; color: #FFFFFF;">
sudo journalctl -u pi-topd
sudo journalctl -u pi-topd --no-pager
sudo journalctl -u pi-topd -b
</pre>

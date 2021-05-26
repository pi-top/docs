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

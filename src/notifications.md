# 🚨 Notifications

pi-topOS comes with a notification system.

The [`pt-notify-send`](https://github.com/pi-top/pt-os-core/blob/master/src/pt-notify-send) command, provided by the `pt-notifications` package, provides an easy-to-use way of sending notifications to the desktop.

`pt-notify-send` is a small wrapper script around [`notify-send.sh`](https://github.com/pi-top/notify-send.sh-deb), a drop-in replacement for the `notify-send` command usually provided by [libnotify-bin](https://packages.debian.org/buster/libnotify-bin) - with the ability to update and close existing notifications.

`pt-notify-send` makes it easy to run the command from anywhere - the environment is dynamically taken care of for you, such as the currently active user who is using the active display.

Visually, pi-topOS uses [`Xfce4-notifyd`](https://packages.debian.org/buster/xfce4-notifyd) - a simple, visually-appealing notification daemon for Xfce that implements the Freedesktop.org Desktop Notifications Specification.

# VNC(Virtual Network Computing) Configuration

This document is for the user who want to connect and use VNC remote display on Cocoan GPU Servers, the required softwares, libraries and other needed almost have been installed. If the VNC is installed a server you use, you can skip installation and check configurating VNC environment on your own account and have a nice work!

## 1. Installation

First, We need to install VNC and other necessary software. you can follow the below lines.

- **For Ubuntu 16.04**

```
$ sudo apt update && sudo apt upgrade

$ sudo apt install ubuntu-desktop gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal

$ sudo apt install tightvncserver
```

- **For Ubuntu 18.04**

```
$ sudo apt update
$ sudo apt upgrade -y
$ sudo apt install xserver-xorg-core
$ sudo apt install tigervnc-standalone-server tigervnc-xorg-extension tigervnc-viewer
```

## 2. Configure VNC environment of your account.

The very first thing you need to do is setting password if you use vnc first time on your server.

```
$ vncpasswd
Password:
Verify:
```

Run VNC server to make sure you are having done well. If there is no problem, then kill.

```
$ vncserver
$ vncserver -kill :\*
```

And then, we need to configure VNC environment. all you need to do is open `~/.vnc/xstartup` and modify it same as the uploaded `xstartup` files. you need to follow your OS system version.

- **For Ubuntu 16.04**

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &

# Resolution Preset
xrandr -s 1600x1200 
```

- **For Ubuntu 18.04**

```
#!/bin/sh
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
vncconfig -iconic &
dbus-launch --exit-with-session gnome-session &
```

## 3. Run your own VNC session and kill your unnecessary session.

That is all. execute the below command line to open vnc session. VNC port start from 5901 and 800x600 resolution is the defualt.

```
## Open vnc session with Specific port.
$ vncserver -localhost no -geometry 1920x1080 -depth 24 :9
```

When you want to kill a session you open, give the port that you use.

```
$ vncserver -kill :11111
$ vncserver -kill :9 # which means 5909
```

You may forgot your port if you had open port long times ago. the you can check listening ports with below command line.

```
$ netstat -plnt | grep vnc
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN      1445/Xtightvnc
tcp        0      0 0.0.0.0:5902            0.0.0.0:*               LISTEN      1895/Xtightvnc
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      1445/Xtightvnc
tcp        0      0 0.0.0.0:6002            0.0.0.0:*               LISTEN      1895/Xtightvnc
```

you can find a port you want to kill among them. this will show you your own listening ports. only superuser can see every listening ports.
---
layout: post
title: Hacking your reMarkable
tags: reMarkable
---

reMarkable is Linux and partially FOSS. This means that it can be easily accessed and customized. For the moment, I'm trying to fix some minor problems of the device. I'm going to update this post with the solutions I came up with.

![My reMarkable](https://scontent-mxp1-1.xx.fbcdn.net/v/t1.0-9/23244558_1507194149366233_5813161295301580330_n.jpg?oh=900a0b2aeb4bba7e0118bd7005a1bf5a&oe=5A698410)


## SSH conncetion

If you check the **rM** menu on the **About** session, you can check which is the username and password you can use to remotely accessing it via `ssh root@10.11.99.1`.

# Activating the tablet HTTP view

When I received my tablet, I tried to use the device's HTTP interface 10.11.99.1, but `nmap -sT -v 10.11.99.1` claimed that only a SSH port was opened. Then I had to surf the file system: I recognized that the `/etc/` folder containes the `remarkable.conf`: besides some clear saved passwords (WiFi, log-in pin, root's password and so forth), you can recognize the `WebInterfaceEnabled=false` parameter. Just change it to `true` and reboot your device to make the web interface start. The web user interface's source code is available at `/usr/share/remarkable/webui/`.
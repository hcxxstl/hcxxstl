---
layout: post
title: Screen Commands
author: terry
categories: bash
excerpt_separator: <!--more-->
---

This article is about the usage of `screen` command. This command is a terminal multiplexer.

<!--more-->

## You can use it for

* Run command in a seperate session in the background
* Display multiple session in one terminal window
* Keep jobs running after logging out remote server
* Share a session with other user

## Frequently used commands

```bash
# Show sessions
$ screen -ls
No sockets found in /var/run/screen/S-tianlisong.

# Start a new session (with name)
$ screen
$ screen -S one

# Detach
$ ^a d

# Show sessions
$ screen -ls
There are screens on:
        1581.pts-4.qce-alveo01  (Detached)
        37977.one       (Detached)
2 Sockets in /var/run/screen/S-tianlisong.

# Reattatch (according to name/id)
$ screen -r
$ screen -r one
$ screen -r 1581

# End session
$ exit
$ ^d
```

## References

* [How To Use Linux Screen, Linuxize](https://linuxize.com/post/how-to-use-linux-screen/)
* [How to Use Linux’s screen Command, How To Geek](https://www.howtogeek.com/662422/how-to-use-linuxs-screen-command/)
* [How to use GNU SCREEN, youtube](https://www.youtube.com/watch?v=I4xVn6Io5Nw)

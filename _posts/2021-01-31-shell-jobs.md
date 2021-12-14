---
layout: post
title: Manage jobs in shell
author: terry
categories: shell
excerpt_separator: <!--more-->
---

This page contains some **hack**s I learned and used during my study and work to manage jobs in shell. I applied them mostly because they are **cool** or useful. These hacks help me to feel cool myself. I write them down here in the hope that they can make your work easier.
<!--more-->

*on* **31/Jan/2021**

## Run jobs without `stdout` messages

While developing hardware with Vivado, you would probably get a lot of `stdout` messages. To make your stdout clean while keeping those messages in a file, you can:

```bash
# to run command while keeping your stdout clean
$ command > command.log 2>&1 &
[1] 27736

# then check your running job
$ jobs -l
[1]+ 27736 Running                 make installip > installip.log 2>&1 &
```

Here you out put the `stdout` into file `command.log` and output your `stderr` as `stdout`.

> `>&` is the syntax to redirect a stream to another file descriptor - `0` is `stdin`, `1` is `stdout`, and `2` is `stderr`.

References:

* [In the shell, what does “ 2>&1 ” mean?, Stackoverflow](https://stackoverflow.com/questions/818255/in-the-shell-what-does-21-mean)
* [How to Run Linux Commands in Background, Linuxize](https://linuxize.com/post/how-to-run-linux-commands-in-background/)

## Keep job running after exiting shell

When you are developing on a remote server over `ssh`, a time-consuming job might be pretty annoying. Because it occupies a shell window for nothing and make you unable to shut down your laptop. To solve this, you can use:

```bash
# list current jobs
$ jobs -l
[1]+ 27736 Running                 make installip > installip.log 2>&1 &

# disown your job with job id
$ disown %1

# now this job is not own by you
$ jobs -l
```

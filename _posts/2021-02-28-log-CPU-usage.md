---
title: Log CPU Usage
auther: terry
layout: post
categories: shell
excerpt_separator: <!--more-->
---

This post is about how to monitor and log CPU usage with simple commands on Linux.
<!--more-->

## Command `top`

The command `top` can show both the current running process and the hardware resources usage.

Here are some simple usage of `top`:

```shell
$ top

# show usage per cpu core
$ top
1

# filter by user
$ top
u <user_name>

# filter by expression
$ top
o COMMAND=<command_of_interest>

# to save configuration to ~/.toprc
$ top
1
W
```

## To monitor/log CPU usage

### Monitor CPU usage of a command

```shell
$ top -c -p $(pgrep -d',' -f iperf)
# show top with COMMAND=iperf
```

### Show CPU per core usage

```shell
# first change configuration
$ top
1
W
# then display the per core usage
$ top -bn 1 | grep -P "^(%|top)"

```

### Log CPU usage to a file

```shell
# save top 10 most CPU hungary process to file ps.log every 5 seconds
$ while true; do (echo "%CPU %MEM ARGS $(date)" && ps -e -o pcpu,pmem,args --sort=pcpu | cut -d" " -f1-5 | tail) >> ps.log; sleep 5; done

# Simply save the uptime info to file uptime.log every 1 seconds
$ while true; do uptime >> uptime.log; sleep 1; done
```

<!-- TODO: ### Wrap it all -->

## References

* [filter processes listed based on processname, StackOverflow](https://stackoverflow.com/questions/12075591/top-c-command-in-linux-to-filter-processes-listed-based-on-processname)
* [How to log CPU load?, AskUbuntu](https://askubuntu.com/questions/22021/how-to-log-cpu-load)

---
layout: post
title: Alveo design flow
author: terry
categories: Xilinx
excerpt_separator: <!--more-->
---

TODO: This article contains some useful info for Alveo design flow.
<!--more-->

## Commonly Used

TODO

## Account

```shell
# Set username globally
$ git config --global user.name "terry"

# Set email address globally
$ git config --global user.email "name@gamil.com"
```

* [Getting Started, git](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

## Info

```shell
# Get repo URL
$ git config --get remote.origin.url
https://github.com/hcxxstl/fpga-network-stack.git

# More infomation
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/hcxxstl/fpga-network-stack.git
  Push  URL: https://github.com/hcxxstl/fpga-network-stack.git
  HEAD branch: master
  Remote branches:
    master        tracked
    xilinx-tcp-ip tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

## Submodule

TODO

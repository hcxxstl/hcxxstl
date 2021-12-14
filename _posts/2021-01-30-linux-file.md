---
layout: post
title: Linux file related commands
author: terry
categories: shell
excerpt_separator: <!--more-->
---

This post is about some commands related to file in Linux.
<!--more-->

*on* **30/Jan/2021**

## Find files

To find a file that matches a regular expression, you can use:

```shell
$ find . -name '<expression>'

# example
$ find . -name '*.exe'
./hello_world.exe
```

So this basically find you all files with `.exe` file extension in your current `.` directory.

## Print the directory tree

*on* **01/Feb/2021**

```shell
# print all the structure for current dir
$ tree .

# print only folders
$ tree -d
.
├── build
│   └── CMakeFiles
│       ├── 3.16.3
│       │   ├── CompilerIdC
│       │   │   └── tmp
│       │   └── CompilerIdCXX
│       │       └── tmp
│       ├── CMakeTmp
│       └── my_hello.dir
└── src

# print only 2 layers deep
$ tree -L 2
.
├── build
│   ├── CMakeCache.txt
│   ├── CMakeFiles
│   ├── cmake_install.cmake
│   ├── Makefile
│   └── my_hello
├── hello_world.exe
└── src
    ├── CMakeLists.txt
    └── hello_world.cpp
```

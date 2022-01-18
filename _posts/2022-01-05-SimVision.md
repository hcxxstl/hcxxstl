---
layout: post
title: SimVison Guide
author: terry
categories: cadence
excerpt_separator: <!--more-->
---

This article introduces how to use SimVision, which is an HDL simulation tool by Cadence. This article includes basic operations and some tips.
<!--more-->

## To Start

```shell
$ simvision waves.shm/ &

```

## Windows

1. **Design Browser**: Scope and signals
2. **Waveform Window**
3. **Source Browser**
4. Schematic Tracer
5. more...

One can easily trace one signal and jump between these windows by clicking the **`Send To`** buttons on the upper right of the toolbar (or right-clicking/double-clicking).

## Shortcuts

| Category | Operation | Shortcut |
|----------|-----------|----------|
| Waveform | Zoom in x | `i` |
| Waveform | Zoom out x | `o` |
| Waveform | Zoom full x | `=` |
| Navigate | Next edge | `Ctrl`+`]` |
| Navigate | Prev edge | `Ctrl`+`[` |
| Edit     | Create group | `Ctrl`+`g` |
| Edit     | Create bus   | `Ctrl`+`b` |
| Edit     | Ungroup | `Ctrl`+`Shift`+`g` |
| Window | Send to waveform | `Ctrl`+`w` |
| Format | Radix Hex | `Ctrl`+`Shift`+`h` |
| Format | Radix Bin | `Ctrl`+`Shift`+`b` |
| Format | Radix Dec | `Ctrl`+`Shift`+`d` |

## Customize

**To edit fonts**
1. Create file `Xdefault` in `~/.simvision/`, or copy the file `/share/cdssetup/simvision/app-defaults/SimVision` as it
2. Add `Simvision*Font` line (which controls the default font) to it as the following scripts

```
! global settings 
Simvision*foreground: black 
Simvision*background: #dfdfdf 
Simvision*Font: -courier-medium-r-normal--12-------*
Simvision*SrcBrowser.fixedFont: --courier-medium-r-normal--12- 
Simvision*SrcBrowser.valueFont: --courier-medium-r-normal--10-
```

## References

* [SimVision Quick Introduction to Major Windows](https://www.youtube.com/watch?v=_TzFkAcOR5s)
* [How do I change the font size in NCSIM gui?](https://stackoverflow.com/questions/24055278/how-do-i-change-the-font-size-in-ncsim-guihttps://www.xilinx.com/html_docs/xilinx2019_2/vitis_doc/Chunk1252764274.html#ariaid-title21)
* [Improving SimVision Fonts for Ubuntu
](https://community.cadence.com/cadence_blogs_8/b/sd/posts/simvision-fonts-for-ubuntu)

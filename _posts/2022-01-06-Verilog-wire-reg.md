---
layout: post
title: Verilog wire or reg for input and output
author: terry
categories: verilog
excerpt_separator: <!--more-->
---

This article explains whether we should use wire or reg for input and output.
<!--more-->

## Difference

> If you plan to assign your output in sequential code, such as within an `always` block, declare it as a `reg` (which really is a misnomer for "variable" in Verilog). Otherwise, it should be a `wire`, which is also the default.



## Explain

* > An output reg `foo` is just shorthand for `output foo_wire; reg foo; assign foo_wire = foo`.

* > `input wire` and `output wire` are the same as `input` and `output`: it's just more explicit.

## References

* [Using wire or reg with input or output in Verilog](https://stackoverflow.com/questions/5360508/using-wire-or-reg-with-input-or-output-in-verilog)

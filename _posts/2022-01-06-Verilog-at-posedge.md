---
layout: post
title: Verilog `@(posedge clk)`
author: terry
categories: verilog
excerpt_separator: <!--more-->
---

This article explains and compares several `@(posedge clk)` statements.
<!--more-->

## Compare

```Verilog
always @(posedge clk) begin
    // codes block 1
end
```

```Verilog
always begin
    @(posedge clk);
    // codes block 2
end
```

```Verilog
@(posedge clk) begin
    // codes block 3
end
```

```Verilog
@(posedge clk);
// codes block 4
```

**The first snippet**: Execute code block whenever at `(posedge clk)`.

**The second snippet**: Only used in procedural block (in testbench). It behaves the same as the first snippet.

**The third snippet**: Only used in procedural block (in testbench). Block the following code block until `(posedge clk)`. When the posedge arrives, execute code block.

**The fourth snippet**: It behaves the same as the third snippet.

## References

* [What is the difference between @(posedge clk) begin](https://verificationacademy.com/forums/systemverilog/what-difference-between-posedge-clk-begin-end....-and-posedge-clk)

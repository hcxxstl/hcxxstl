---
layout: post
title: Vivado ila for Vitis flow on Alveo
author: terry
categories: xilinx
excerpt_separator: <!--more-->
---

This article introduces how to implement ila modules and debug with it for hardware design. This is within the scope of Alveo platform and Vitis design flow. For other devices and flows, the process could be a little different.
<!--more-->

## [Overall Steps](https://www.xilinx.com/html_docs/xilinx2020_1/vitis_doc/debuggingapplicationskernels.html#jld1547475955135)

1. Add debug IP to the kernel.
2. Modify the host program to pause at the appropriate point.
3. Set up the environment for hardware debug.
4. Iteratively run the hardware debug flow using the following process:
   a. Run the host program and pause at the appropriate point to enable setup of the ILA triggers.
   b. Open the Vivado hardware manager and connect to the XVC server.
   c. Set up ILA trigger conditions for the design.
   d. Continue execution of the host program.
   e. Inspect kernel activity in the Vivado hardware manager.

## Step 1: Add ILA IP in kernel (manually)

A simple example is shown in the code below. The data width of signals of interest should be aware.

```verilog
    // ILA module instance
    ila_0 i_ila_0 (
        .clk(ap_clk),     // input wire          clk
        .probe0(txData),  // input wire [511:0]  probe0  
        .probe1(rxData),  // input wire [511:0]  probe1 
        .probe2(cnt),     // input wire [31:0]   probe2 
    );
```

After adding the ILA module to the HDL code, the ILA IP should also be generated. For example in the tcl script:

```tcl
create_ip -name ila -vendor xilinx.com -library ip -version 6.2 -module_name ila_0
set_property -dict [list CONFIG.C_PROBE2_WIDTH {32} CONFIG.C_PROBE1_WIDTH {512} \
CONFIG.C_PROBE0_WIDTH {512} CONFIG.C_NUM_OF_PROBES {3} CONFIG.C_EN_STRG_QUAL {1} \
CONFIG.C_ADV_TRIGGER {true} CONFIG.C_INPUT_PIPE_STAGES {1} ] [get_ips ila_0]
```

For more information of the parameters, check table 2-2 in [this guide](https://www.xilinx.com/support/documentation/ip_documentation/ila/v6_2/pg172-ila.pdf).

## Step 2: Modify host code

In order to enable the ILA, host program should pause after the binary programmed and before the kernel run. Either a breakpoint or an wait function can achieve this. Here we insert the `wait_for_enter` function to host code.

```c++
    ...
    // program binary
    cl::Program program(context, devices, bins);
    cl::Kernel krnl_vadd(program,"krnl_vadd_rtl");

    wait_for_enter("\nPress ENTER to continue after setting up ILA trigger...");

    // run kernel
    //Allocate Buffer in Global Memory
    ...
    //Copy input data to device global memory
    ...
    //Set the Kernel Arguments
    ...
    //Launch the Kernel
    q.enqueueTask(krnl_vadd);
    ...
```

## Step 3: Setup hardware debug

```shell
# Use the debug_hw script to launch the xvc_pcie and hw_server apps
$ debug_hw --xvc_pcie /dev/xvc_pub.<driver_id> --hw_server
# Or for Alveo it should be
# To check what driver you have, use
$ ls /dev/xfpga/xvc_pub*
$ debug_hw --xvc_pcie /dev/xfpga/xvc_pub.<driver_id> --hw_server

# For example
$ debug_hw --xvc_pcie /dev/xfpga/xvc_pub.u14081.0 --hw_server
launching xvc_pcie...
/opt/apps/xilinx/Vivado/2019.2/bin/xvc_pcie -d /dev/xfpga/xvc_pub.u14081.0 -s TCP::10200
launching hw_server...
/opt/apps/xilinx/Vivado/2019.2/bin/hw_server -sTCP::3121

****************************
*** Press Ctrl-C to exit ***
****************************
```

Make sure to keep the hardware server running while launching ChipScope.

## Step 4: Debug flow

First run the host program.

```shell
$ ./host network.xclbin
...
Device[1]: program successful!

Press ENTER to continue after setting up ILA trigger...
```

Then Launch Vivado Design Suite (ChipScope).

```shell
$ debug_hw --vivado --host <host_name> --ltx_file ./_x/link/vivado/vpl/prj/prj.runs/impl_1/debug_nets.ltx
# For example
$ debug_hw --vivado --host qce-alveo01 --ltx_file debug_nets.ltx
```

In the Vivado you can see the ILA module. Setup and run ILA trigger for your debugging.

Finally press Enter to continue running the host program (enqueue the kernel).

Now you can observe the captured waveform. Iterate this step 4 as required.

## References

* [Debugging During Hardware Execution](https://www.xilinx.com/html_docs/xilinx2019_2/vitis_doc/Chunk1252764274.html#ariaid-title21)
* [Hardware/Software Debugging, xilinx.github.io](https://xilinx.github.io/xup_compute_acceleration/debug_lab.html)
* [Vivado Programming and Debugging, UG908](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_3/ug908-vivado-programming-debugging.pdf)
* [Integrated Logic Analyzer v6.2, IP Product Guide](https://www.xilinx.com/support/documentation/ip_documentation/ila/v6_2/pg172-ila.pdf)

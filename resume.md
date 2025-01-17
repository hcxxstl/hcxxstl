---
layout: page
author: terry
title: RESUME
#permalink: /resume/
---

---

## **EDUCATION**

<center><img align="right" src="imgs/resume/TUDelft_Logo.png" height="60"/></center>

**Delft University of Technology (TUD)**  
Master of Science in Electrical Engineering, Microelectronics track  
*Sept. 2019 – Nov 2021*  
GPA: **7.86**/10

<center><img align="right" src="imgs/resume/sjtulogoblue.png" height="60"/></center>

**Shanghai Jiao Tong University (SJTU)**  
Bachelor of Science in Electronic Science and Technology  
*Sept. 2015 - Jun. 2019*  
GPA: **84.6**/100

<br>

---

## **THESIS PROJECTS**

**RoCE based 100Gbps RDMA network stack on FPGA hardware**  
Master thesis
*Advisor: Dr. Zaid Al-Ars*  
*Nov. 2020 - Nov. 2021*

- Investigated the alternative solutions in terms of transport layer models and architectures for RDMA network stack for FPGA implementation
- Studied and contributed to an open source 100 Gbps FPGA network stack IP in High Level Synthesis with C++
- Developed an open source 100 Gbps RoCE v2 stack for Alveo FPGA platforms which supports direct memory access to both on-board high bandwidth memory (HBM) and host memory
- Made measurements of throughput and latency for the designed RDMA stack on Xilinx Adaptive Compute Cluster FPGAs at ETH Zurich, which achieves a goodput around 90-95 Gbps and a round trip latency under 4.5 ms for both RDMA READ and WRITE operations

The project is publically available on the [Github repositiry](https://github.com/hcxxstl/Vitis_RoCE).

<center><img src="imgs/resume/roce_top.png" width="400"/></center>
<br>

**Simulation and Design of Micro-Ring Optical Filters**  
Bachelor thesis
*Advisor: Dr. Xuhan Guo*  
*Apr. 2018 - Sept. 2018*  

- Simulated a bandpass optical filter based on micro-ring resonator structure in Lumerical FDTD Solutions, achieving a narrow passband of 0.8nm and a relatively large roll-off in the 1550 nm communication band (C-band)
- Deduced and modeled the coupling relationship based on transfer matrix method in MATLAB, and simulated Vernier micro-ring structure as well as Coupled-Ring Optical Waveguide (CROW) structure
- Designed a Vernier micro-ring resonator filter in Lumerical MODE Solutions, achieving a free spectral range larger than 45nm with an extinction ratio greater than 30dB, and an insertion loss below 3dB in the C-band
- Designed a cascaded micro-ring-based reconfigurable filter consists of eight micro-rings, achieving an FSR of 45 nm, bandwidth adjustment range from 0.43 to 1.25 nm, and central wavelength adjustment range covering the entire FSR
- Optimized this reconfigurable photonic filter in MODE Solutions simulator, and achieved an insertion loss less than 1dB, an extinction ratio larger than 25dB and passband flatness smaller than 0.5dB over all configurations

<center><img src="imgs/resume/photonic_filter.png" width="300"/></center>
<br>

---

## **SELECTED RESEARCHES & COURSE PROJECTS**

**Big Data Processing using Spark and Kafka**  
*Advisor: Dr. Zaid Al-Ars*  
*Sept. 2020 - Nov. 2020*

- Developed an application to process OpenStreetMap (OSM) data using Spark in Scala and improved its scalability
- Packaged the application and deployed it on Amazon EMR clusters to process the entire OSM data set (76 GB)
- Implemented a streaming application to filter and count records using Kafka Streams DSL and Processor API

<center><img src="/imgs/resume/bigdata.gif" width="300"/></center>
<br>

**SystemC Neural Network**  
*Advisor: Dr. Ir. Rene van Leuken*  
*May. 2020 - Jul. 2020*

- Implemented a one-layer artificial neural network (ANN) on SystemC Virtual Platform (SCVP) in SystemC and C++
- Optimized hardware resource usage of this design by replacing fix point numbers with integers
- Optimized the weight update algorithms by implementing backpropagation, which achieved an accuracy of 81% identifying the MNIST digits on the single layer structure with limited training set (64 images)

<center><img src="imgs/resume/vlsi_mnist.png" width="200"/></center>
<br>

**Design of Time-to-Digital Convertor (TDC)**  
*Advisor: Dr. Morteza Alavi*  
*Feb. 2020 - Apr. 2020*

- Designed the structure of a 5-bit high resolution time-to-digital convertor with 2-D Vernier structure
- Developed the schematic design of the 2-D Vernier TDC from transistor level in Cadence Spectre
- Optimized the TDC with buffers and redundant blocks, achieved a time resolution of 6.07ps and good linearity with both integral and differential non linearity below 0.3 in 90nm CMOS technology

<center><img src="imgs/resume/tdc.png" width="200"/></center>
<br>

**SoC Design Based on rVEX Reconfigurable Architecture**  
*Advisor: Dr. Sorin Cotofana*  
*Nov. 2019 - Feb. 2020*  

- Performed Design Space Exploration (DSE) simulations via VEX toolchain, optimized the area and performance of the rVEX processor considering computational resources and memory configurations for different applications
- Designed a SoC based on rVEX architecture to implement target operations, and performed DSE of it on FPGA
- Designed a dual-core VEX processor to efficiently run the target benchmarks in parallel with minimum idle resources, and optimized the design to be well-balanced among occupied area, execution cycle and power consumption

<center><img src="imgs/resume/dualcore.png" width="300"/></center>
<br>

**Design of Discrete-Time Fully Differential Amplifier**  
*Advisor: Dr. Klaas Bult*  
*Nov. 2019 - Jan. 2020*  

- Designed a discrete-time fully differential amplifier of a given gain-boosting architecture in 0.18um CMOS in LTSpice
- Performed AC simulation, transient simulation and noise simulation for this differential amplifier
- Sized the transistors in the amplifier and achieved 60dB accuracy in 9.78ns with power dissipation of 0.79mW

<center><img src="imgs/resume/amplifier.jpg" width="200"/></center>  
<br>

**Optimization of Advanced Computing Systems**  
*Advisor: Dr. Zaid Al-Ars*  
*Sept. 2019 - Nov. 2019*  

- Implemented simple SIMD extension (AVX), OpenMP and OpenCL to accelerate benchmarks
- Applied CUDA for to accelerate an imaging processing pipeline (including ripple effect and Gaussian blur) in C++
- Implemented CUDA to improve the performance of a k-means clustering algorithm, and achieved a speedup of 90X

<center><img src="imgs/resume/ACS.png" width="200"/></center>
<br>

**Design of Stabilized DC Power Supply**  
*Advisor: Dr. Yan Yuan*  
*Sept. 2017 - Jan. 2018*  

- Built a closed-loop stabilized DC power supply using nonsynchronous voltage-mode controller chips, which had a characteristic of a wide input range, an output voltage swing less than 0.8% and an efficiency of 94% at 2A output
- Developed a human-machine interface for the power supply on the Texas Instruments MSP430 Launchpad, with switch debouncing, manual voltage setting, precise output current monitoring, and power distribution balancing functions

<center><img src="imgs/resume/3A.jpg" width="200"/></center>
<br>

**Medical Image Segmentation Based on Machine Learning**  
*Advisor: Dr. Yu Qiao*  
*Oct. 2016 - Oct. 2017*  

- Programmed gray scale gradient boundary extraction and distortion correction algorithms by MATLAB
- Implemented reinforcement learning and traditional active-shape-model algorithm to build an interactive medical image segmentation platform, which enabled doctors to optimize segment results with their experience

<br>

**Wireless Remote-Control System Based on Microcontroller**  
*Advisor: Dr. Xiaodong Wu*  
*Mar. 2016 - Jun. 2016*  

- Established wireless TCP communication between mobile phone App and ESP8266 chip over Wi-Fi connection
- Designed a voice interactive system using an Arduino Mini board and an MP3 decoding board
- Built a remote-control system with these two parts, and realized stable connection in 40 meters

<br>

---

## **INTERNSHIP**  

**FPGA Design Intern at Shanghai Qian Ting Network Technology Co., Ltd.**  
*Research and Development Department*  
*Sept. 2018 - Feb. 2019*  

- Developed a format conversion module on Xilinx Spartan-3 FPGA board in Verilog with clock domain crossing method
- Built a two-way Ethernet communication module by Modelsim and Xilinx ISE, connecting the PHY chip and FPGA through Gigabit Media-Independent Interface (GMII), with CRC-32 redundancy check and packet capture abilities
- Designed an asynchronous DSP interface on Spartan-3 FPGA board, and realized read/write operations with the DSP
- Integrated the Ethernet and DSP modules into a whole, realizing network routing and packet filtering functions
- Designed an synchronous CPU interface on Gaowin FPGA board, and realized communication with an ARM chip

<br>

---

## **MISCELLANEOUS**

**Software**
MATLAB, Vivado/Vitis, Modelsim, Cadence Spectre, LTspice

**Programming**  
Verilog, System Verilog, VHDL, Python, C/C++, bash, Git, MakeFile, LaTeX, TCL scripts, CUDA, Spark

**Scholarship**
KTH scholarship 2019 (30 out of 2000, didn't accept)

**Award**
The 3rd Prize of SJTU Texas Instruments Cup Electronic Design Competition in 2017

**Volunteer**
Constructed the facilities of a farm in Australia Trentham for a month in 2017

**Coursera**
Java for Android, Machine Learning, HTML CSS and JavaScript

**Hobbies**
Skateboarding (President of SJTU Sk8 Club), Rubik's Cube (3*3 in 15 seconds), Photography

<br>

---
<center>Updated on 14/12/2021</center>

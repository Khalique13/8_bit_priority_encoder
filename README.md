# 8 bit Priority Encoder (dvsd_pe) RTL to GDS flow 
In this project complete RTL to GDS flow has been done for 8 bit Priorty Encoder

# Contents
- [Design Overview](#design-overview)
- [IP specs Provided](#ip-specs-provided)
- [Verilog behavioral design](#verilog-behavioral-design)
- [Openlane](#openlane)
	- [Installation](#installation)
	- [Running OpenLane](#running-openlane)
	- [Synthesis](#synthesis)
	- [Floorplan](#floorplan)
	- [Placement](#placement)
	- [Routing](#routing)
	- [Final Layout](#final-layout)
- [Pre-layout](#pre-layout)
	- [Simulation](#simulation)
	- [Performance](#performance)
- [Post-layout](#post-layout)
	- [Synthesis](#synthesis)
	- [Simulation](#simulation)
- [Instant count](#instant-count)
- [Steps to reproduce and explore the design](#steps-to-reproduce-and-explore-the-design)
- [Keys to remember](#keys-to-remember)
- [Area of improvement](#area-of-improvement)
- [References](#references)
- [Acknowledgement](#acknowledgement)


### Design Overview

![Slide2](https://user-images.githubusercontent.com/80625515/130179293-b7b03b4c-2feb-40a6-814a-31af06acc3cd.PNG)

### IP specs provided

![Slide4](https://user-images.githubusercontent.com/80625515/130180121-a4e5d529-bb6d-4ed3-a265-aad5030f82f7.PNG)

### Verilog behavioral design

## OpenLane 

OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, Fault and custom methodology scripts for design exploration and optimization.
For more information check [here](https://openlane.readthedocs.io/)

### Installation

```
git clone https://github.com/The-OpenROAD-Project/OpenLane.git
cd OpenLane/
make openlane
make pdk
make test # This a ~5 minute test that verifies that the flow and the pdk were properly installed
```

For detailed installation process, check [here](https://github.com/The-OpenROAD-Project/OpenLane)

### Running OpenLane

`make mount`
- Note
	- Default PDK_ROOT is $(pwd)/pdks. If you have installed the PDK at a different location, run the following before `make mount`:
	- Default IMAGE_NAME is efabless/openlane:current. If you want to use a different version, run the following before `make mount`:

The following is roughly what happens under the hood when you run `make mount` + the required exports:

```
export PDK_ROOT=<absolute path to where skywater-pdk and open_pdks will reside>
export IMAGE_NAME=<docker image name>
docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) $IMAGE_NAME
```

You can use the following example to check the overall setup:

`./flow.tcl -design spm`



### Synthesis

### Floorplan

### Placement

### Routing

### Final Layout

## Pre-layout

### Simulation

  Terminal snap (To perform pre-layout simulation)
  
  ![pre_layout_sim_ter](https://user-images.githubusercontent.com/80625515/130185638-d927ef90-81d7-4642-b03f-10dfdc7c3ce1.png)

  GTKWave output waveform
  
 ![pre_layout_sim](https://user-images.githubusercontent.com/80625515/130185662-662b9542-c5c1-4584-9d7f-da6d140f4aad.png)

### Steps to reproduce Pre-layout simulation

 Open terminal in your system (preferred Ubuntu OS)

```
git clone https://github.com/Khalique13/dvsd_pe_1v8.git
cd dvsd_pe_1v8/pre_layout/
iverilog -o dvsd_pe dvsd_pe.v test_dvsd_pe.v
./dvsd_pe
gtkwave dvsd_pe.vcd
```

### Performance

## Post-layout

### Synthesis



### Simulation

Terminal snap (To perform post-layout simulation)

![post_lay_sim_term](https://user-images.githubusercontent.com/80625515/130189588-be201db3-9f21-4d12-9055-9806750a0675.png)

GTKWave output waveform

*`To be uploaded soon some bugs`*

### Steps to reproduce Post-layout simulation

 Open terminal in your system (preferred Ubuntu OS)

```
git clone https://github.com/Khalique13/dvsd_pe_1v8.git
cd dvsd_pe_1v8/post_layout/
iverilog -o gls gls.v primitives.v sky130_fd_sc_hd.v
./gls
gtkwave gls.vcd
```

## Instant count

## Steps to reproduce and explore the design

## Keys to remember

## Area of improvement

## References



## Acknowledgement

- [Kunal Ghosh](https://github.com/kunalg123), Founder, VSD Corp. Pvt. Ltd
- [Mohammad Khalique Khan](https://github.com/Khalique13), Bachelor of Technology in Electronics & Communication Engineering, Aliah University

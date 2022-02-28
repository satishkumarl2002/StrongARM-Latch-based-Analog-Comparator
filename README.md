# StrongARM-Latch-based-Analog-Comparator
This repository presents the design of a StrongARM Latch based Analog Comparator implemented using Synopsis Custom Compiler on 28nm CMOS Technology.
# Table of Contents
 * [Introduction](#Introduction)
 * [The StrongARM Latch](#The-StrongARM-Latch)
 * [RS Latch](#RS-Latch)
 * [Tools Used](#Tools-Used)
 * [Pre-Layout Schematics and Simulations](#Pre-Layout-Schematics-and-Simulations)
 * [Netlist of the Circuit](#Netlist-of-the-Circuit)
 * [Observations](#Observations)
 * [Author](#Author)
 * [Acknowledgements](#Acknowledgements)
 * [References](#References)

# Introduction:
A differential Comparator is an integral part of analog to
digital converters where it is used to perform quantisation and
sampling. A standard opamp as a comparator is not preferred
for these applications as it reduces the maximum sampling
frequency that could be attained. In this design, a strongArm
latch is used as the comparator core and is chosen as the core
for this circuit because it consumes zero static power, produces
full swing rail to rail outputs, requires single clock phase and
provides higher sampling bandwidth. The strongArm latch
stage is followed by a RS latch which is used to hold the
output data during precharge phase of the strongArm latch.

# The StrongARM Latch:
The StrongARM latch topology finds wide usage as a sense amplifier, a comparator, or simply a robust
latch with high sensitivity.The latch consists of 5 NMOS and 5 PMOS transistors. Transistor M1 and M2 form the input differential pair, transistor M3-M6 form the cross coupled inverters, S1-S4 are the charging transistors and M7 is the tail current transistor. Operation of the latch consists of three phases, Reset, Amplification, and Regeneration.

During the reset phase, input clock is low which turns of the tail current transistor M7 and the input differential pair M1 and M2 is disconnected. Nodes P,Q,X,Y charge to Vdd through the charging transistors S1,S2,S3,S4 which are on when clock is low. The entire circuit draws no current during reset phase as the cross coupled inverter are turned off.

The amplification phase begins as soon as clock goes from low to high turning off the charging transistors S1,S2,S3,S4 and
turning on the tail current transistor M7, thereby activating the input differential pair M1,M2 which draws current
proportional to the input provided at gate terminals of M1 and M2. The current drawn by M1 and M2 discharges the nodes P and Q which were precharged to Vdd.

The regeneration phase begins when nodes P and Q discharge to Vdd-Vthn , turning M3 and M4 (NMOS transistors of cross coupled inverters) on. Nodes X and
Y then begins discharging from Vdd. Since they form a cross
coupled inverter with positive feedback, the node which discharges faster (i.e the one which draws higher current) and falls down to zero while the other node regenerates back to Vdd, depending on the polarity of input differential votalge. Hence it effectively performs the action of a comparator.
<p align="center">
<img src="StrongARM Latch Reference Diagram.png"></br>
  Fig. 1: StrongARM Latch 
</p>

# RS Latch
During the reset phase , the output nodes of the StrongArm Latch is precharged to Vdd, hence erasing its previous output which leads to the current output not representing a valid logic level, which confuses the subsequent stages. This issue is resolved by the addition of a reset-set latch connected to the output terminals of the StrongARM latch. The RS latch can change its state only if one of the output of the previous stage falls to zero. This latch then retains the state as the StrongARM latch enters reset phase. 
<p align="center">
<img src="StrongARM Latch followed by RS Latch.png"></br>
  Fig. 2: StrongARM Latch followed by RS Latch 
</p>

# Tools Used:

Synopsys Custom Compiler:</b></br>
The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

Synopsys Primewave:</b></br>
PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

Synopsys 28nm PDK:</b></br>
The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.

# Pre-Layout Schematics and Simulations:

## Schematics:
### StrongARM Latch:
Implementation of StrongARM Latch Cell:
<p align="center">
<img src="StrongARM Latch Schematic.png"></br>
  Fig. 3: StrongARM Latch Schematic 
</p>
<p align="center">
<img src="StrongARM Latch Symbol.png"></br>
  Fig. 4: StrongARM Latch Symbol 
</p>

### RS Latch:
Implementation of RS Latch Cell:
<p align="center">
<img src="RS Latch Schematic.png"></br>
  Fig. 5: RS Latch Schematic 
</p>
<p align="center">
<img src="RS Latch Symbol.png"></br>
  Fig. 6: RS Latch Symbol 
</p>


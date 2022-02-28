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
The latch consists of 5 NMOS and 5 PMOS transistors.
Transistor M1 and M2 form the input differential pair, transistor M3-M6 form the cross coupled inverters, S1-S4 are the
charging transistors and M7 is the tail current transistor. Operation of the latch consists of three phases, Reset, Amplification,
and Regeneration.
During the reset phase, input clock is low which turns of
the tail current transistor M7 and the input differential pair
is disconnected. Nodes P,Q,X,Y charge to Vdd through the
charging transistors which are on when clock is low.The entire
circuit draws no current during reset phase.
The amplification phase begins as soon as clock goes
from low to high turning off the charging transistors and
turning on M7 thereby activating M1,M2 which draws current
proportional to the differential input provided at gate terminals
of M1 and M2 which discharges the nodes P and Q.
The regeneration phase begins when nodes P and Q discharge to Vdd-Vthn , turning M3 and M4 on. Nodes X and
Y then begins discharging from Vdd. Since they form a cross
coupled inverter with positive feedback, eventually one node
regenerates back to Vdd and the other node falls to zero,
depending on the polarity of input differential votalge.

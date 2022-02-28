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

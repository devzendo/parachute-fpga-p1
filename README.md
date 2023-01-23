# parachute-fpga-p1

## What is this?
My first attempt at a soft-core CPU design, targetting the inexpensive Lattice iCEstick FPGA
evaluation board. Intended to become a VERY cut-down version of an early integer-only Transputer, which can run eForth.
It's to be a _transputerette_. Since this FPGA is tiny, and I just want to get a very simple microcoded CPU system started, there will be no multitasking or scheduling, and possibly only a single link to connect to the host system. It'll run a very small subset of essential instructions. If I can get this working, I'll upgrade to a larger FPGA and start the P2 which will be more complete.

## Project Status
Project started January 2023. Currently in its initial study phase. 

# Overview
This is my first attempt at digital design; I've never built a CPU before, and I'm a beginner at VHDL/Verilog/FPGA.
Expect many rookie errors and much confusion.

This is part of the Parachute Project - I already have an emulator of a 32-bit, integer-only Transputer, and am working on a port of eForth for it. I have a comprehensive macro assembler for Transputer assembly language, and want to target some real hardware, rather than just the emulator. The only problem is that Transputers are no longer produced, hardware is hard to come by, and needs legacy PC systems to support it. I want a cheap Transputer system built from modern components. This is one way to get there.


## Downloads
There aren't any yet. There will be for the first release, but that won't be any time soon. When there is something worth demonstrating, I'll commit a bitstream release here.

# Development

## Current activities
For information on current development activities, please see the [TODO file](TODO.md) file.

## Technology
The hardware description language in use here is Verilog. I may switch to Spinal-HDL as I become more familiar with FPGA development, if this makes a significant improvement.

I'm using the free, licensed iCEcube2 / Diamond Programmer tools from Lattice. It should be possible to synthesise, route and build a bitstream using APIO/Yosys/IceStorm tools, but I haven't got these working yet.

## Source directory structure
The source is split into the following directories:

(there isn't any yet!)

docs - documentation, rough notes, references.

## Building

# Documentation
Please see the 'docs' directory. 

# Acknowledgements

# Bibliography
* Structured Computer Organization - Tanenbaum, 3rd edition.
* Digital Design using VHDL - Dally, Harting, Aamodt.
* Verilog by Example: A Concise Introduction For FPGA Design - Readler.
* The Transputer Handbook - Graham, King.



# License, Copyright & Contact info
This code is released under the Apache 2.0 License: http://www.apache.org/licenses/LICENSE-2.0.html.

(C) 2023 Matt J. Gumbley

matt.gumbley@devzendo.org

Mastodon: @M0CUV@mastodon.radio

http://devzendo.github.io/parachute

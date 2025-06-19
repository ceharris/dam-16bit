dam-16bit
=========

This repository contains KiCad sources for 16-bit digital acquisition
module suitable for use as passive bus monitor. It is designed to be
compatible with the [icm7212m-display](https://github.com/ceharris/icm7212m-display). Using this module and the complementary display module, a 16-bit 
input can be continuously displayed in hexadecimal notation on the 
4-digit LED display.

This module uses a NE555 timer in astable mode to produce a 1 kHz 
clock. At each clock pulse a 2-bit counter is incremented. The counter
outputs are used as address lines for one unit of a 74HC139 dual 2-to-4
decoder circuit. The active low chip select outputs of the decoder are
connected to the chip select inputs of two 74HC244 octal buffers. The
74HC244 consists of two 4-bit buffer units which can be independently 
selected. The outputs of the 4-bit buffer units on each of the 74HC244
circuits are connected to the B0..3 outputs for the display module.

The 2-bit counter outputs are also used to provide the DS1 and DS2 
(digit select) inputs for the display module.

With this design, the sample rate for the 16-bit inputs is approximately
250 Hz. With each clock pulse, four bits of the input are sampled and
the result is sent to the corresponding display digit.


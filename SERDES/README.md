# High-speed Serializer and Deserializer design

## Introduction
The project is a part of a radiation high-speed communication module design, which includes 16b/20b encoder, 20:1 serializer, transmitter, receiver, comma detector & word alignment, 1:20 deserializer, 20b/16b decoder, all custom designed in Cadence Virtuoso SCL 180 nm technology.<br/>
This part of the project is the design of 20:1 serializer and 1:20 bit deserializer using half rate architectures.<br/>
Although 20 parallel bits are serialized into one single serilized data stream, the clock requirement is of 10x clock of the reference and not 20x. This was the major achievement of the project, where high speed dezerialization is achieved without the use of lower speed clock. A similar scheme is used for the deserialier side.

## 1. 20:1 Serializer

![SER Block Diagram](https://github.com/mukutdnath/Projects/blob/main/SERDES/diagrams/ser.jpg?raw=true)

The input is 20-bit parallel data, while the output is corrsponding serialized data stream. Thus, the 100 Mega bits per second 20 bit input is serialized to 2 Giga bits per second (serialized data stream has 20 times more speed than the parallel data streams). <br/>
The clock synthesizer is a PLL based 10X clock generator which is used to serialize the first 10 bits and the second 10 bits simultaneously and then the two 10:1 serialized data are further serialized using the positive and negative levels of the 10X clock respectively, to get the final 20:1 serialized output. (**half rate architecture**)<br/>
The mux is realised using two transmission gate switches that operate on the original 10x clock and its inverted output so that during positive half of the clock output is connected to the first 10:1 serial data and during negative half the output is connected to the second 10:1 serial data. The operation is described in detail in the further sections.

### 1.1 Clock Synthesizer

![Clock Synthesizer Block Diagram](https://github.com/mukutdnath/Projects/blob/main/SERDES/diagrams/clock_synth.jpg)

This Phase Locked Loop generate the 10X clock required for the serializer operation. The VCO output is fed to a clock divider, which is a synchronous state machine and divides the input clock by 10. The clock divider output is locked with the reference clock of 100 MHz and thus the clock divider input (VCO Output) is 1 GHz which is the PLL synthesized 10X clock.

### 1.2 10:1 Serializers

### 1.3 Expected output waveforms
![Expected Timing Diagram](https://github.com/mukutdnath/Projects/blob/main/SERDES/diagrams/ser_timing.png)

# High-speed Serializer and Deserializer design

## Introduction
The project is a part of a radiation high-speed communication module design, which includes 16b/20b encoder, 20:1 serializer, transmitter, receiver, comma detector & word alignment, 1:20 deserializer, 20b/16b decoder, all custom designed in Cadence Virtuoso SCL 180 nm technology.<br/>
This part of the project is the design of 20:1 serializer and 1:20 bit deserializer using half rate architectures.<br/>
Although 20 parallel bits are serialized into one single serilized data stream, the clock requirement is of 10x clock of the reference and not 20x. This was the major achievement of the project, where high speed dezerialization is achieved without the use of lower speed clock. A similar scheme is used for the deserialier side.

## 20:1 Serializer

![SER Block Diagram](https://github.com/mukutdnath/Projects/blob/main/SERDES/diagrams/ser.jpg?raw=true)

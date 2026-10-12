---
layout: page
title: Protocol Emulator
description: A reprogrammable, SRAM-programmed protocol engine chip for Tiny Tapeout.
importance: 8
category: hardware
---

I am designing an SRAM-programmed [protocol emulator](https://github.com/WilliamZhang20/protocol-emulator), a Tiny Tapeout chip built for Jane Street's ASIC design challenge. A host loads bytecode into on-chip SRAM, streams payload bytes through FIFOs, and starts a deterministic, bit-level engine. The hardware is protocol-neutral, so UART, SPI, I²C, JTAG, and other line patterns are defined by the program rather than fixed in silicon.

The design has two real-time action lanes with their own shifters, counters, timers, and configurable CRC/LFSR, plus a dispatcher that arbitrates shared pins and FIFO ports. It is verified with cocotb simulation and formal checks with mutation testing.

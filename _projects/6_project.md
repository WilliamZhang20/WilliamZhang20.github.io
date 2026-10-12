---
layout: page
title: RISC-V Multi-Core SoC
description: A multi-core RV32I CPU and integrated GPU written from scratch in SystemVerilog.
importance: 6
category: hardware
---

I am designing a multi-core [RISC-V CPU](https://github.com/WilliamZhang20/riscv-cpu) with an integrated GPU, written from scratch in SystemVerilog.

So far it has a 5-stage pipelined RV32I core, L1 instruction and data caches, a shared L2, coherence between cores, and a NoC-style interconnect. I am working on non-blocking caches, MSI coherence, and superscalar issue.

---
layout: page
title: OxCamlGPU
description: A GPU programming DSL that compiles OxCaml kernels to PTX.
importance: 5
category: systems
---

I am building [OxCamlGPU](https://github.com/WilliamZhang20/OxCamlGPU), a GPU DSL on top of OxCaml's high-performance programming model. Kernel authors write ordinary OxCaml functions, and the compiler carries type-derived facts into a GPU IR, verifies them, and emits PTX.

A Hopper GEMM kernel written in the DSL reaches parity with cuBLAS at 8192³ TF32 on an H100. It is still an active prototype that supports a narrow kernel subset.

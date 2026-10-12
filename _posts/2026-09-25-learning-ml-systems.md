---
layout: post
title: How I Would Learn ML Systems If I Could Start Over
date: 2026-09-04 00:01:00
description: An introspection and self-organization of my knowledge in my career area
tags: [gpu architecture, gpu progarmming, ml systems]
categories: [asic]
pseudocode: true
---

In 2024, around the time when the NVIDIA stock price started skyrocketing, I became very curious about how the GPUs worked, so I began learning about ML and ML systems, entirely from the internet.

For the first couple weeks, all I did was watch a few disparate YouTube videos. Then for the next few months, I started studying the (old version) of the CUDA C++ Programming guide, where I learned kernel programming and basic kernel optimization tricks such as shared memory, tensor cores, swizzling, etc. That slowly led me up the stack to quantization, PyTorch and compilers. At the same time, I studied TPU architecture as well.

But when I had finished the above, it was the end of 2025, and agents could write decent kernels and code very easily, and optimize things much faster than I could. So most of 2026 has ended up being a lot of vibe coding and superficially understanding the process. The huge downside of this unhealthy habit can be explained by the famous Richard Feynman [quote](https://www.quora.com/What-did-Richard-Feynman-mean-when-he-said-What-I-cannot-create-I-do-not-understand), "What I cannot create, I do not understand." Moreover, simply prompting ChatGPT/Claude/Gemini non-systematically became doomed to fail, as I was even outsourcing the synthesis of the knowledge.

So now I have decided to create a proper synthesis of the knowledge needed to not only help myself and others gain a solid grip of the topic at all layers of the stack, but also make it a good recipe for success in relevant interviews requiring ML performance optimization. I will assume the reader has basic knowledge of how neural network models, but instead of discussing how training algorithm makes the model learn, I'll discuss how to make ML operations work well on hardware.

### 1) GPU Architecture Fundamentals

Warps

SMs

Tensor Cores

Memory Hierarchy

### 2) Optimizing Performance on a GPU

Roofline Analysis

Leveraging Tensor Cores
- tiling
- vectorization
- memory coalescing

Kernel Fusion

CUDA Graphs

### 3) Algebraic Reformulation

Example - loss function

Flash Attention

### 4) Quantization

### 5) Compilers

### Conclusion

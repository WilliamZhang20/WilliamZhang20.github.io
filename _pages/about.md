---
layout: about
title: about
permalink: /

profile:
  align: right
  image: headshot_cropped.JPG
  image_circular: false # crops the image to make it circular

selected_papers: false # includes a list of papers marked as "selected={true}"
social: false # includes social icons at the bottom of the page

announcements:
  enabled: false # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

I am a third-year (3B) computer engineering student at the [University of Waterloo](https://uwaterloo.ca/).


## Main Focus

I work on making machine learning run effciently on hardware, through:

- **GPU optimization**: writing and tuning GPU kernels
- **ML models**: understanding and optimizing how models learn and map onto hardware
- **Compilers**: lowering and optimizing kernels and models for GPUs and other domain-specific architectures

## Also Exploring

Areas I'm passionate about outside of my main focus:

- **RTL and chip design**: CPU and ASIC design. Taped out a chip on Tiny Tapeout, another one in progress!
- **Convex optimization**: applied in personal projects and open-source contributions to [CVXPY](https://www.cvxpy.org/). I am also supplementing my knowledge by taking [CO 255](https://uwflow.com/course/CO255) at school.
- **FPGA CAD**: open-source [CAD tools](https://github.com/verilog-to-routing/vtr-verilog-to-routing) that apply optimization to placement and routing

## Experience

<ul>
  <li class="mb-3">
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>NVIDIA</span>
      <span class="text-nowrap ms-3">Jan. 2027 - Apr. 2027</span>
    </div>
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Software Engineer Intern</span>
      <span class="text-nowrap ms-3"><em>Toronto, Canada</em></span>
    </div>
  </li>
  <li class="mb-3">
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Cerebras Systems</span>
      <span class="text-nowrap ms-3">May 2026 - Aug. 2026</span>
    </div>
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Software Engineer Intern</span>
      <span class="text-nowrap ms-3"><em>Toronto, Canada</em></span>
    </div>
  </li>
  <li class="mb-3">
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Trend Micro</span>
      <span class="text-nowrap ms-3">Sept. 2025 - Dec. 2025</span>
    </div>
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Software Engineer Intern</span>
      <span class="text-nowrap ms-3"><em>Ottawa, Canada</em></span>
    </div>
  </li>
  <li class="mb-3">
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Ford Motor Company</span>
      <span class="text-nowrap ms-3">Jan. 2025 - Apr. 2025</span>
    </div>
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Software Engineer Intern</span>
      <span class="text-nowrap ms-3"><em>Ottawa, Canada</em></span>
    </div>
  </li>
  <li class="mb-3">
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Ford Motor Company</span>
      <span class="text-nowrap ms-3">May 2024 - Aug. 2024</span>
    </div>
    <div class="d-flex justify-content-between align-items-baseline w-100">
      <span>Software Engineer Intern</span>
      <span class="text-nowrap ms-3"><em>Ottawa, Canada</em></span>
    </div>
  </li>
</ul>

## Open-Source Contributions

Some of the open-source projects that I have contributed to include:
- [CVXPY](https://github.com/cvxpy/cvxpy), a Python-embedded modelling language for convex optimization problems, with over 4M downloads/month. Originates from a research project at Stanford University.
  - [Huber scale parameter](https://github.com/cvxpy/cvxpy/pull/3344): extended the `huber` atom with a scale parameter `t`, adding a new perspective-based atom `t·huber(x/t, M)` that stays convex and DCP-compliant, so users can jointly optimize over the scale of a robust loss.
  - [Dual feasibility checks](https://github.com/cvxpy/cvxpy/pull/3441): implemented constraint residuals across CVXPY's constraint types to enable post-solve checks of dual feasibility, helping users verify solver results.
- [CVXPYlayers](https://github.com/cvxpy/cvxpylayers), a Python library for convex optimization-based layers in deep neural networks, compatible with PyTorch, JAX, and MLX.
  - [Custom solver interface](https://github.com/cvxpy/cvxpylayers/pull/233): enabled plugging custom solvers, such as generated C code from CVXPYgen, into differentiable layers in both PyTorch and JAX. The generated C solver can enable 3.3x faster solve times than default paths.
- [DCCP](https://github.com/cvxgrp/dccp) (Discplined Convex-Concave Programming), a convex heuristic for solving nonconvex problems.
  - [DPP compatibility](https://github.com/cvxgrp/dccp/pull/118): parametrized the linearization so each iteration updates parameters instead of rebuilding the problem, resulting in 30% speedups.
- [Tilus](https://github.com/NVIDIA/tilus), a GPU domain-specific language by NVIDIA that provides explicit low-level control and hardware abstraction.
  - [Hopper matmul examples](https://github.com/NVIDIA/tilus/pull/159): wrote a progression of Hopper GEMM kernels reaching ~108% of cuBLAS throughput on an H100 (FP16, 8192³).
  - [Faster compilation](https://github.com/NVIDIA/tilus/pull/163): cut autotuning re-run latency via dependency-aware specialization keys and compiler fingerprinting, taking a full 12-schedule first call from ~3.1 s to ~65 ms (~48x).
- [Mirage Persistent Kernel](https://github.com/mirage-project/mirage), a megakernel compiler for models being developed by the CMU Catalyst Lab. Work still in progress!
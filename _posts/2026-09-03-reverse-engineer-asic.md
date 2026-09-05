---
layout: post
title: Reverse Engineering a Star Battle ASIC
date: 2026-09-04 00:01:00
description: Reverse engineering a Star Battle ASIC from its GDS layout.
tags: [asic, reverse engineering]
categories: [asic]
pseudocode: true
---

My solution to the [Jane Street challenge](https://blog.janestreet.com/can-you-reverse-engineer-an-asic/).

The code I wrote to solve the puzzle can be found in the [asic-puzzle-2026 repository](https://github.com/WilliamZhang20/asic-puzzle-2026).

When I encountered the challenge, my first step was to extract the netlist from the GDS. Naturally, this is because the GDS is the output of place-and-route tools, which take the RTL, produce a netlist, and then lay out this netlist onto the standard cell library.

So I wrote a simple Python script using Claude called `gds_extract.py` in the `tools` folder of my repository. It uses the gdstk and Shapely libraries to extract the netlist from the `puzzle.gds` input file. The gdstk library obtains the GDS hierarchy, polygons, cell references, transformations, and labels. Subsequently, Shapely merges touching conductor geometry independently on each routing layer. That way, different polygons for the same wire are semantically united. Finally, a disjoint-set/union-find data structure connects those components through contacts and vias. This is because a single net can traverse numerous polygons and multiple layers.

{% include figure.liquid path="assets/img/asic/netlist_placement_actual.png" class="img-fluid rounded z-depth-1" alt="Recovered gate-level netlist with logic, flip-flop, output, success, and shared regions highlighted" caption="The extracted netlist, laid out to reveal the major logic and output regions of the ASIC." zoomable=true %}

The result of this pipeline is a gate-level netlist. Its purpose is to map each cell instance to a numeric net and indicate the nets connecting them. For example, if “cell_17.Y” and “cell_18.A” were the same logical wire, they would have the same mapped value. Note that wires separated by a gate do not count as the same net.

Given this netlist, Claude helped me write `simulate_netlist.py` to simulate its Boolean behavior. It adapts the netlist from the SKY130 PDK library to common elements in combinational and sequential logic. For example, in the PDK, some cells are compound gates, such as “a2110”; there are also AND-invert-OR compounds. Moreover, there are various types of flip-flops. Ultimately, all of these were topologically evaluated on rising clock edges to simulate the actual input-to-output mapping, leading to the final step of solving the puzzle.

Running the example input gave `success = 0`, as expected. The output bytes, when mapped to ASCII characters, produced the phrase “TRY AGAIN.”

To figure out what input would generate `success = 1`, I used the Z3 SAT solver and wrote the solving code in `solve_challenge.py`. It turns each of the 121 input bits into Boolean variables whose values must be solved to obtain a successful output. The symbolic input bits are then propagated through the netlist, one clock cycle at a time. This builds Boolean expressions that the solver must satisfy. At the end of the netlist, the success constraint is added to Z3. The result is the input sequence that produces success. Once obtained, the program adds a clause eliminating the previous input sequence, but that resulted in UNSAT, showing that the solution is unique.

{% include figure.liquid path="assets/img/asic/register_dependencies.png" class="img-fluid rounded z-depth-1" alt="Dependency graph connecting the ASIC input signals to banks of flip-flops" caption="The recovered register-dependency graph shows how enable and input signals fan out through the sequential state banks." zoomable=true %}

That solution is the sequence:

```text
000000010101000010000000000001010101000000000000101000000100000100000010000010
1000010000000100000010000010010001010000000
```

{% include figure.liquid path="assets/img/asic/recovered_puzzle.png" class="img-fluid rounded z-depth-1" alt="Recovered eleven-by-eleven Star Battle board divided into colored regions" caption="The recovered 11 × 11 board, with the chip’s gate-level state influence grouped into regions A–K." zoomable=true %}

{% include figure.liquid path="assets/img/asic/solved_puzzle.png" class="img-fluid rounded z-depth-1" alt="Solved eleven-by-eleven Star Battle board with two stars in every row, column, and region" caption="The unique valid solution: 22 stars, with two in every row, column, and region and no touching stars." zoomable=true %}

The final answer from the output under that successful input stream was `(* TWO STARS *)`, which is the syntax of a comment in OCaml, Jane Street’s most commonly used language. The output also confirms that the ASIC is a Star Battle game, and the input is a row-major representation of the grid.

## Extracting the Easter Eggs

The first two easter eggs were found by feeding all zeros and all ones into the input sequence. These produced the output ASCII strings “EMPTY SKY” and “BIG BANG,” respectively.

Another easter egg was found in the example inputs file, which contained two separate 121-bit input sequences. The chip was fed one, disabled, and then fed the other; both produced “TRY AGAIN.” Splitting each 121-bit stream into eleven rows of eleven bits, then interpreting columns 0–6 of each row as a 7-bit, least-significant-bit-first ASCII character, produced:

```text
attempt 1: "The night s"
attempt 2: "ky awaits  "

Together:
"The night sky awaits  "
```

The final easter egg was found using `enumerate_messages.py`. It also uses the Z3 solver, but instead of simply solving for a successful input sequence, it enumerates all possible output sequences by invalidating previous output sequences. This strategy revealed a new output that had not been caught previously: the case where each row, column, and diagonal had two stars, but the stars touched, violating one of the rules. This led to the output string “TWO NOT TOUCH.”

{% include figure.liquid path="assets/img/asic/two_not_touch.png" class="img-fluid rounded z-depth-1" alt="Star Battle board with two touching stars and the output TWO NOT TOUCH" caption="The touching-stars Easter egg: a board satisfying the star counts but violating the no-touching rule." zoomable=true %}

## Conclusion

I learned a lot about GDS internals, netlists, and SAT solvers from this challenge, and I look forward to the ASIC design and tapeout challenge coming up in the future!

William Zhang

---
layout: post
title: "Advent of Code 2025: 12 Days"
date: 2025-12-16 10:00:00 -0500
categories: technology
---

This was my third year participating in
[Advent of Code](https://adventofcode.com/), and I enjoyed it more than ever.
The big change this year was that it ran for 12 days instead of 25. I didn't
expect that to matter much, but it really did.

## 12 Days Instead of 25

I love Advent of Code, but the 25-day run is a real commitment. Even when the
problems are fun, the daily pace adds pressure in the middle of an already busy
month.

The 12-day format felt much more sustainable. It kept the "advent calendar"
energy while lowering the chance of falling behind and never catching up. I was
able to finish all of the puzzles this year (24 stars) without the end-of-month
burnout I sometimes feel.

## A Good Mix of Puzzle Types

The shorter run didn't feel like a watered-down version of Advent of Code. The
problems covered a surprisingly wide range of ideas.

A few that stood out for me:

- **Day 6** had me parsing a grid of digits and operators into large numbers and
  combining them with a running `+`/`*` operation.

- **Day 7** was a neat beam-splitting simulation where part two turned into a
  counting problem (tracking how many beams end up in each lane).

- **Day 8** was essentially "connect points in 3D by distance" and ended up
  feeling like a clustering / minimum-spanning-tree style problem.

- **Day 10** combined a "Lights Out"-style button puzzle (shortest sequence via
  BFS) with a more math-heavy second part where I set up a system of equations
  and searched for a minimum non-negative integer solution.

- **Day 11** was about counting paths through a graph, with extra state to
  enforce constraints (paths that must pass through specific nodes).

- **Day 12** looked like it was heading toward an NP-hard packing problem, but
  the actual input had enough structure that a simple area-based shortcut was
  sufficient.

If you're curious, my solutions are in
[my Advent of Code repo](https://github.com/paulvanbrenk/advent-of-code), under
`src/2025/`.

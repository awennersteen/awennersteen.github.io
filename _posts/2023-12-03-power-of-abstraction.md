---
title: 'Power of abstraction'
date: 2023-12-03
permalink: /posts/2023/12/abstractions/
description: "A reflection on how abstraction enables better software and mathematical thinking, managing complexity and improving performance through structured concepts."
excerpt: "This essay discusses the role of abstraction in programming and mathematics, showing how focusing on high-level structures can manage complexity, enhance readability, and inform performance-oriented design."
tags:
  - mathematics
  - quantum
  - quantum-computing
  - quantum-software
  - software
  - software-architecture
---

## Abstractions and performance

Abstractions are useful for guiding thoughts.

Abstractions allow us to manage complexity and focus on high-level concepts rather than getting bogged down by intricate details.
When programming, abstractions enable developers to create modular and reusable code by defining clear interfaces and encapsulating the inner workings of functions or objects.
This not only makes the code more readable and maintainable but also facilitates collaborative development as different team members can work on separate components without needing to understand the entire system.

In mathematics, abstractions such as numbers, functions, and spaces allow for the exploration of complex ideas and theorems without being hindered by the specific properties of individual cases.

Category theory, often referred to as "the mathematics of mathematics,"
takes the concept of abstraction to an extreme by focusing on the relationships between mathematical structures rather than the structures themselves.
Categories are collections of objects and morphisms that adhere to specific composition laws.
This turns out to be a powerful perspective that allows mathematicians to identify and study similarities between seemingly unrelated topics.

In programming this means that if at the end of the day we focus on performance
the abstractions we work in should translate back to that. For example if what we're working
on ends up being data and the main blocker is the [AoS vs SoA](https://en.wikipedia.org/wiki/AoS_and_SoA) problem then
either it should be solved for the abstraction, or the abstraction needs to allow to user to solve it.

Optimizations should always be pushed to the extrema. I.e we should do optimization at the low level
(SIMD, cache, math primitives) or we should do it at a high level (exposing parallelism at a high level,
ensuring that we don't do more work than we have to). My experience is that trying to optimize
at the middle layers is a terrible idea and usually ends up with subpar performance and system.

This idea of abstractions can be extended to other areas too of course. At Pasqal one of my
principal projects was Qadence. The idea there was that we wanted to free up our algorithm researchers
time by building things into the framework they work in, and to have this standardized so that it
would be easier to move between code-bases. This was extra important as we wanted to move things
from one paradigm ("digital quantum computing") towards one that was better suited for the hardware
that the company would be able to release in the coming years ("Analog" and "Digital Analog" quantum computing).

In this case the optimizations were three-fold. One was the hardware itself, out of bounds for me.
The other two were native differentiability at a high level, and custom numerical backends (also differentiable).
Comparing to my early days at Qu & Co / Pasqal what is rather fascinating is that now it takes us mere seconds
(in Python!) to run experiments that would have taken a couple of days back then.
Zero percent of that performance gate was achieved by low-level optimization as our numerical backends are most certainly
inferior to the ones we used back then. (Ignoring the hard work by the PyTorch developers of course!)

I did make one great mistake with Qadence though, which was to largely ignore the middle.
As the project matured the shortcuts taken in the middle ended up causing great engineering costs
and poor developer experience. Making it harder to modify means it's also become a bottleneck for performance
as it's harder to optimize the full stack.
Luckily others were keen to sort that out and we'll release a v2 of
Qadence where this middle-layer will be greatly improved.

One thing which has bothered me about quantum computing after working on emulation with tensor networks
is that once there is a presence of structure the problem tends to be exposed to tensor network methods
and other cleverness. Abstractions, and their compositions, is inherently structured.
Even if the threat of the tensor network theorists will have a limit as systems get bigger it's still a concern.
I see it as a sign we're not pushing the system to the maximum.

Perhaps there is an analogy here to the AoS vs SoA problem...

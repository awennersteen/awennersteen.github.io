---
title: "Qadence @ POPL24"
collection: talks
type: "Talk"
permalink: /talks/2024-01-20-PlanQC24-Qadence
venue: "Institution of Engineering and Technology"
date: 2024-01-20
location: "London, UK"
---

The Fourth International Workshop on Programming Languages for Quantum Computing (PLanQC 2024) at the
51st ACM SIGPLAN Symposium on Principles of Programming Languages (POPL 2024).

It was fascinating attending this conference, very different from what I usually attend and also gave som very interesting ideas.
My main two takeaways from the dive into the theory of programming languages are that
1. Programming languages influence how you think and how you write code. And that you can take this mindset with you when writing libraries as at the end of the day the line between a library and a domain specific languages embedded in the main language you work in (e.g. Python) is rather small.
2. By exploiting type definitions it becomes rather easy to prove correctness, and perhaps even verify your program input.

The second point here was very influenced by the POPL session on probabilistic programming languages. There, graphs are a central component of the language/problem.
By encoding the vertex position in a unique way, the syntax for forming graphs and verifying their correctness becomes much simpler.
Indeed, this manner of thinking where you really focus on proving correctness is a lesson I've already noticed having influenced my programming style.

Lastly, I gave a talk on our new quantum programming framework / language during the workshop dedicated to the topic of quantum programming languages.

You can watch the presentation on [YouTube](https://www.youtube.com/watch?v=cXIll6l7S1s&t=8797s),
the slides are available on [the conference webpage](Checkhttps://popl24.sigplan.org/details/planqc-2024-papers/4/Qadence-a-differentiable-interface-for-digital-analog-programs).

Qadence is open source and you find it on our [GitHub](https://github.com/pasqal-io/qadence).
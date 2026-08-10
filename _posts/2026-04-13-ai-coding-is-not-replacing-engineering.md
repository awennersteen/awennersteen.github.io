---
title: "AI Coding Is Not Replacing Engineering"
date: 2026-04-13
permalink: /posts/2026/04/ai-coding-is-not-replacing-engineering/
description: "AI coding shifts engineering value toward scaffolding, architecture, documentation, and judgment rather than replacing software engineering."
excerpt: "AI coding is remarkably good at getting projects off the ground, but robust software still depends on engineering judgment: structure, documentation, architecture, and knowing where things will break."
categories:
  - "Technical Leadership & Engineering Practice"
tags:
  - LLM
  - architecture
  - performance
---

I’ve now done a few AI coding projects with the latest generation of models that have come out in 2026, and I must say I'm pretty excited!

Some examples that stand out for me are my own AI agent, a game I wrote for my partner to use in her job as an English teacher, and a computer vision system for intelligent video analytics. What really struck me is how good AI agents are at getting these kinds of projects off the ground. In the video analytics project, it took me a couple of hours to largely replicate a proof of concept that had taken several man-months to set up some years ago.

I do not think the lesson is that software engineering no longer matters, though. I think it is almost the opposite. The value shifts. What seems to matter a lot is setting up the base scaffolding properly. By that I mean the structure, the technologies to be used, and ideally pointing the agent to some relevant example code. When that is done well, these systems are much more effective. When it is not, they happily generate a lot of rubbish. That part still feels very engineering-heavy to me. Next, what becomes important is iterating using “business knowledge”—having a concrete design in mind. Without that, the agent will again happily generate a lot of rubbish.

The next part is maybe even more interesting. For apps that are not immediately going into large-scale production, you can suddenly have a much looser and more collaborative development process. In the Pasapalabra example, I showed it to my wife and she could make great progress in the middle by herself without being technical. Then I stepped back in at the end to make the final changes, make sure the code was something I could support in future if needed, and make sure it would not just fall over.

That last part matters because there is still a big difference between something that works in a demo and something that will survive contact with reality. Cf. the joke:

> A QA engineer walks into a bar. Orders a beer. Orders 0 beers. Orders 99999999999 beers. Orders a lizard. Orders -1 beers. Orders a ueicbksjdhd.
>
> First real customer walks in and asks where the bathroom is. The bar bursts into flames.

That still applies! AI is very good at getting you to something that looks finished. That is not the same thing as something robust, supportable, or even remotely appropriate for the task!

Moving towards real applications with history, the picture changes again. A lot of the same lessons still apply, but more strongly. Structure remains paramount, because otherwise the AI agents can go a bit crazy. If the boundaries are unclear, if the modules are muddled, if the conventions are inconsistent, they will happily amplify that mess at speed. Good structure always mattered, but with AI it becomes even more important because the system will aggressively exploit whatever shape you give it, good or bad.

Documentation also becomes much more important. Not just external documentation, but documentation in the code itself. Clear names, clear interfaces, clear comments where the intent is not obvious, and clear examples of how things are supposed to be used. A human engineer can often infer a lot from partial context, or know who to ask. The model cannot. If the rationale is not written down somewhere, it is much less likely to reconstruct it reliably. In that sense, AI coding makes poor documentation more expensive. On this side of things I've been generating code in many languages, and I'm really starting to like modern typed languages like Rust in this era. The traits can serve as excellent boundaries for the AI agent.

To me, the real shift is not that AI replaces software engineering. It is that it changes where engineering earns its keep. Less in raw implementation. More in framing, scaffolding, documentation, taste, architecture, and knowing where things are likely to break. The bottleneck moves up a level. And once you get into real applications, it becomes even clearer that software is not just code. It is structure, accumulated judgement, and a large amount of tacit knowledge that we have historically carried around in people's heads.

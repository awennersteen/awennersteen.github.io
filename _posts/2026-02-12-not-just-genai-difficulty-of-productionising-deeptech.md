---
title: "Not just GenAI: difficulty of productionising deeptech"
date: 2026-02-12
permalink: /posts/2026/02/not-just-genai-difficulty-of-productionising-deeptech/
description: "Explore why deeptech and GenAI adoption stalls beyond the lab, and how high performance computing trends and infrastructure shape real products."
excerpt: "GenAI prototypes are fast, but production outcomes depend on evaluation, data boundaries, and cost control. I connect today's enterprise adoption slowdown to older deep-tech patterns, including lessons from production video analytics and the AI infrastructure arms race."
feature_text: "Why production outcomes lag demos, and how evaluation, data boundaries, and cost control determine adoption."
categories:
  - "Industry & Technology Trends"
tags:
  - AI
  - GenAI
  - deeptech
  - product
---

I started writing this in summer/autumn 2024, when the “ChatGPT moment” analogy was being thrown around for everything, and revisited it in early 2025 after Jensen's comments on the usefulness of quantum computing. Finishing it now in 2026, the core thesis still feels right: the demo is easy, the production system is hard, and the hard part is rarely the model.

GenAI is a great example. Building a prototype that feels magical can take a weekend. Building something that’s:

- reliable,
- measurable,
- safe,
- and cost-controlled,

often takes months, and usually requires product + data + platform work that looks a lot like other deep tech programs.

I was reminded of this by a post from Fulgencio Navarro (we worked together on video analytics at Dive in 2020–2021): deep learning has been “proven” for years, but large parts of video surveillance analytics in production still lean on classical CV because the system costs, operational burden, and real-world variability are unforgiving.

## Why GenAI feels different (at first)

GenAI gives you a powerful “illusion of completeness”: the system can respond to almost any prompt, so it feels like the missing work is just UI polish and scaling.

In reality, the missing work is usually:

- evaluation (how do you know it’s correct enough?),
- data boundaries (what can it see, what must it never see?),
- integration (what systems does it touch, what is the blast radius?),
- and operating costs (tokens, latency, retries, fallbacks).

If you’ve ever worked on a deep tech program, this will sound familiar: the hardest part isn’t a single breakthrough, it’s the system that makes the breakthrough useful.

## The “silent failure” problem

Traditional software fails loudly: exceptions, 500s, timeouts. GenAI often fails quietly: it produces an answer that looks plausible, passes a casual read, and is wrong in a way that only shows up downstream. Or the LLM may not fully follow your instructions, and the format is valid but still not what you expect.

That has two consequences:

1. You need evaluation harnesses and monitoring earlier than you think (offline tests, golden sets, drift tracking).
2. You need product design that anticipates uncertainty (confidence cues, citations where possible, “I don’t know” flows, escalation paths).

This is why so many orgs get stuck in a PoC loop: the system “works” until someone asks for evidence that it works.

## A concrete parallel: video surveillance analytics

Fulgencio’s point (in the context of intrusion detection / line crossing / anomaly detection) maps surprisingly well to today’s GenAI product work:

- **High costs.** Running deep learning continuously in production changes the economics of what used to be “cameras + a recording box”. GenAI has the same story: tokens, GPUs, and latency budgets become product constraints, not technical footnotes.
- **Complexity.** In surveillance, camera placement, lighting, occlusions, tuning, and maintenance become part of “making the model work”. In GenAI, the analogs are data boundaries, retrieval quality, tool integrations, and the operational work needed to keep behavior stable over time.
- **Inconsistent results and marketing noise.** In surveillance, vendors claim “99%+” in controlled settings while real environments break assumptions. In GenAI, the surface area is broader, but the pattern is the same: demos are clean; production inputs are not; evaluation is hard; trust is fragile.

The point isn’t “GenAI is doomed”. It’s that the obstacles to mainstream adoption are often boring systems work, not missing clever prompts.

## Why this is deep tech-ish (even when the model is a commodity)

Even if you treat the model as an API, deploying GenAI at scale needs real infrastructure and operational maturity.

For something like ChatGPT to exist, two things had to be in place:

- the model/training recipe (algorithmic progress),
- and the compute substrate (massive GPU fleets and the software stacks around them).

That second part is a very “deep tech” style dependency: capital-intensive, capacity-constrained, and tightly coupled to hardware supply chains.

This is also where the “enterprise adoption is slower than the hype” narrative shows up. The Information reported that major cloud providers were privately tempering expectations with sales teams, citing cost, output quality, and ROI uncertainty even as the public messaging stayed bullish.

At the infrastructure layer, I like David Cahn’s framing (Sequoia): don’t conflate “AI will matter” with “today’s CapEx is the right speed”. Even if you’re fully optimistic on AI’s impact, it can still be rational to worry about overbuilding too early, especially when architectures change quickly. The counterforce is game theory: hyperscalers can’t easily slow down unilaterally without risking future positioning, so spending escalates as a defensive move.

## A note on the “ChatGPT moment” analogy (quantum vs GenAI)

I keep seeing people talk about a future “ChatGPT moment” for quantum computing. I’m skeptical that this analogy helps.

In my mental model, “ChatGPT moment” wasn’t just one thing going right; it was a stack:

- a product surface that normal people could use,
- a model that was broadly capable,
- and a hardware/software ecosystem that could serve it to millions of people.

Quantum is missing different pieces of the stack (and in a different way): hardware capability, error correction pathways, and a set of applications that are both useful and deployable. There will be a “moment”, but it might not look like a single app suddenly crossing a threshold.

I ended up writing a short note about the “ChatGPT moment” framing after NVIDIA CEO Jensen Huang’s comments on the quantum market. My main reaction wasn’t that quantum “can’t” get there, but that the analogy compresses too many dependencies into one slogan.

## Practical takeaways (if you’re trying to ship GenAI)

If you’re trying to turn a GenAI demo into a product, the steps that seem to matter most are not exotic:

- Pick a narrow scope and define “correct enough”.
- Build an evaluation set before you scale usage.
- Decide what data is in-bounds and enforce it in code (not in a slide deck).
- Put cost and latency budgets in place early.
- Treat outputs as untrusted and validate where you can (schemas, tool calls, UI rendering).
- Invest in support workflows for when it’s wrong (because it will be).

## References

- Fulgencio Navarro (LinkedIn Pulse) on production barriers in video surveillance analytics: https://www.linkedin.com/pulse/12-year-struggle-why-cutting-edge-ai-deep-learning-still-navarro-rgpxf
- LinkedIn post (Lidia Pierre) on why GenAI product work is hard: https://www.linkedin.com/posts/lidia-pierre_ai-genai-llms-activity-7214210019704156160-W5tH
- Gartner press release on “expectations declining” in generative AI (linked to PoC struggles): https://www.gartner.com/en/newsroom/press-releases/2024-06-25-gartner-survey-shows-expectations-for-generative-ai-decline-as-organizations-struggle-to-move-beyond-proof-of-concept
- Business Insider reporting on cooling enterprise demand: https://www.businessinsider.com/generative-ai-enterprise-demand-chill-2024-12
- The Information on cloud providers privately tempering expectations (paywalled): https://www.theinformation.com/articles/generative-ai-providers-quietly-tamp-down-expectations
- David Cahn (Sequoia) – AI Optimism vs. AI Arms Race: https://sequoiacap.com/article/ai-optimism-vs-ai-arms-race/
- My Bluesky post on “ChatGPT moment” framing (after Jensen Huang’s quantum comments): https://bsky.app/profile/awennersteen.bsky.social/post/3lff6lrh3rk2x

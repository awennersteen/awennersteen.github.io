---
title: 'Architecting new projects'
date: 2023-11-01
permalink: /posts/2023/11/architecting
description: "Practical guidance on starting greenfield software projects, including requirement gathering, strategic planning, and balancing technical design with real-world execution."
excerpt: "This post shares insights on initiating new software projects, emphasizing the iterative nature of requirements gathering, stakeholder alignment, and balancing technical ambition with maintainable progress."
tags:
  - software
---


Recently I've helped a few colleagues start greenfield projects for the first time.
I've noticed repeatedly that this is a difficult task for many, and sometimes academics moving into industry feel a bit overwhelmed about trying to write nice code that is up tho our standards.
In this post I want to try to shed some light on how this truly is a iterative process. Especially when what you're making is new and we don't really know how to tackle it.

Architecting a new software project is a challenging endeavor that requires a careful balance of technical acumen,
strategic planning, and effective communication. One of the most critical stages in this process is requirements gathering. 

## The requirements stage

We need to understand what we're building and why. This is the requirements gathering stage.

The requirements gathering stage is the phase where stakeholders' needs and expectations are meticulously documented and analyzed.
This phase is crucial because it clarifies the project's scope, defines its objectives,
and sets the parameters within which the development team will operate.
The goal is to capture a comprehensive picture of what the software should achieve and how it should function,
considering both the current and future needs.

In a regular project this will involve many stakeholders. One common issue is the communication gap between technical and non-technical stakeholders.
Additionally, stakeholders might have conflicting priorities or expectations.
What's extra difficult when building
something purely technical and novel is that it is hard to gather requirements and goals,
and the people usually tasked with doing this
may not have sufficient technical expertise to pull it off.

In an environment where many of those present are fresh out of academia as relatively junior scientists
managing the worldview of those involved is extra challenging. Usability and technical design might be 
some of the first topics that come to mind, but changing the mindset from "minimal publishable novel contribution" to
a fully fledged out project that is maintainable over time is in my experience the most challenging.

I always like to write a design document or RFC where we also utilise a frameworks like MoSCoW (Must have, Should have, Could have, and Won't have) to prioritize requirements.
This helps against scope creep and also in discovering where the biggest technical challenge will be and how to design the Proof of Concept (PoC).
Comparing this explicitly against the closest available products and their shortcomings is crucial.

## The initial POC

In the requirements gathering phase we've identified the primary problem the product aims to solve and the key features that need to be demonstrated.
It is crucial to keep the scope limited to essential functionalities, ensuring that the PoC remains manageable and focused.
It's also important that we make sure to not sweep under the rug the hard parts of the problem. In some sense this is very different
from building a PoC for a startup where these things can often be swept under the rug to be tackled later when funding arrives.

However, one mustn't strive too much for perfection at this stage.
These projects can be very hard to implement and it's easy to get stuck in development for so long that others start to plan around your existence.
Keep complexity low and put in the extra effort to make it easy to hack and extend the product as if you're not ready to respond to user requests for feedback immediately that can kill your progress.

After developing the prototype, it is essential to conduct thorough evaluations and gather feedback from stakeholders.
This includes testing the PoC in real-world scenarios to assess its performance, usability, and scalability.
Engaging with potential users and clients during this phase provides valuable insights and helps identify any gaps or areas for improvement.
I've found it most helpful to really sit down with people at this point and go through things.
In some sense this is the second requirement gathering phase, as it is often first now that people are really able to articulate what they want and need.

## Maintaining the product long term

Is a whole different beast to be tackled in a later post!

---
title: "Microservices are technical debt"
date: 2026-02-11
permalink: /posts/2026/02/microservices-are-technical-debt/
description: "Learn how software engineering best practices help avoid microservices becoming a distributed monolith, and decide when to pay down architecture debt."
excerpt: "Microservices can help when domain boundaries are real and teams need independent deployment. More often they become a distributed monolith with expensive operations and coordination. This post lays out the warning signs and what I would do instead by default."
feature_text: "When microservices help, when they hurt (always), and how to avoid a distributed monolith by defaulting to a modular monolith."
categories:
  - "Technical Leadership & Engineering Practice"
tags:
  - software
  - architecture
  - microservices
---

Microservices are a tool, not a virtue.

I’m going to be intentionally blunt here: in a lot of teams, “microservices” ends up as a long-lived debt position. It feels like progress early on (more repos, more pipelines, more boxes on diagrams), but it often creates coupling you can’t see until you try to change something.

The core failure mode is simple: you build a distributed monolith. The system is split into many deployables, but the product still behaves like one unit: most services must be up for basic functionality, releases are coordinated, and one change cascades across the fleet.

## When microservices help

Microservices can absolutely be the right choice, especially when you have:

- multiple teams that need to ship independently,
- clear domain boundaries that are stable over time,
- uneven scaling needs (one part of the system is 100× hotter than the rest),
- regulatory or security constraints that require isolation

If those are true, microservices can reduce organizational friction and make ownership clearer.
And for several of these, a handful of macro services will probably serve you best.

## Where they hurt (most teams)

What you pay for microservices is not just “network latency”; it’s everything around the network call:

- operational overhead (deployments, alerts, dashboards, runbooks),
- debugging overhead (distributed tracing, correlation IDs, partial failures),
- data pain (transactions, consistency, migrations, reporting),
- and coordination cost (schemas, contracts, versioning, rollback compatibility).

None of that is impossible. It’s just expensive, and it scales with the number of services.

If you don’t have a strong reason to pay that bill, you’re buying complexity on credit.

And don't get me started on startups running Kubernetes.

## Signs you’ve built a distributed monolith

I’ve seen these patterns repeatedly:

- Deployments are “independent” in theory, but in practice require synchronized releases.
- A “simple” feature needs changes in 5+ services.
- Local development needs a mini Kubernetes cluster.
- Incidents are hard to reason about because failures propagate in loops.
- Teams spend more time on platform glue than on product behavior.

If you recognize this, the architecture is not serving you; you’re serving it.

## What I would do instead (by default)

My default recommendation for new products is a modular monolith:

- one deployable,
- internal modules with clear boundaries,
- strict internal interfaces,
- and explicit ownership.

This gets you most of the benefits people want from microservices (separation, clarity, testability) without paying the distributed-systems tax on day one.

When a boundary hardens and the scaling/ownership case is real, then split a service out. Not because it’s fashionable, but because the pressure is measurable.

## Paying down the debt

If you’re already “microservices-first” and it’s slowing you down, the goal is not to make a grand rewrite. The goal is to reduce coupling and make change cheaper.

A few approaches that tend to work:

- Reduce cross-service synchronous calls for critical paths; prefer async boundaries where it fits.
- Identify “shared” libraries and hidden coupling; make dependencies explicit and versioned.
- Reduce the number of places a feature needs to change (this is often a domain modeling problem, not a technical one).
- If a set of services always deploy together and always fail together, consider reducing the service count for that slice of the system.

The intent isn’t to be anti-microservices.
It’s to be pro-change: if an architecture makes change expensive, it will eventually dominate your roadmap.

## References

- YouTube talk referenced in my notes: https://www.youtube.com/watch?v=LcJKxPXYudE
- Martin Fowler on microservices (tradeoffs and characteristics): https://martinfowler.com/articles/microservices.html
- The Grug Brained Developer (a must read) https://grugbrain.dev/

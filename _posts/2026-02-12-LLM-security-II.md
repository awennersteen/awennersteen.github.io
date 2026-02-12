---
title: "Generative AI security-II"
date: 2026-02-09
permalink: /posts/2026/02/genai-security-II/
description: "Learn practical generative AI security lessons from OWASP and Lakera on prompt injection defenses, including input/output controls and monitoring."
excerpt: "A practical follow-up on deploying LLM features: treat the model as untrusted, control both prompts and outputs, and assume cost is a product constraint. I map concrete mitigations to the OWASP GenAI Top 10 (2025) and discuss what to look for in an AI gateway."
categories:
  - "AI & ML Systems"
tags:
  - LLMs
  - GenerativeAI
  - Security
  - prompting
  - prompt-engineering
  - prompt-injection
  - Gandalf
---

This post is a follow-up to [Recreating Gandalf](https://awennersteen.com/posts/2024/07/gandalf/) and [GenAI security](https://awennersteen.com/posts/2024/07/genai-security/). The first two posts were mostly about prompt injection as a concept; this one is more about what I would actually implement if I had to run an LLM feature in production.
This was originally written in summer 2024, but due to human error remained unpublished.

The framing that helped me is to treat an LLM like an untrusted component behind an API boundary. The LLM is powerful, but it is not a policy engine, it is not an authorization layer, and it is not an audit log.

## Why “AI firewalls” and gateways keep showing up

If you look at how vendors describe “AI gateways” / “AI firewalls”, the common idea is boring in a good way: put a reverse-proxy style control point between users and the model so you can enforce policies on both prompts and responses (PII filtering, injection detection, rate limits, cost controls, logging, etc.). The F5 article is a good example of this framing, and it also highlights a key point: you want visibility in both directions, not just “screen the input”. 

The moment you have:

- multiple user populations,
- multiple model providers (OpenAI/Azure/self-hosted),
- real compliance requirements,
- and non-trivial costs,

you will eventually want this to be centralized rather than implemented ad hoc in every application.

## A simple threat model

Before talking about mitigations, the “threat model” I implicitly assume for most enterprise-ish LLM features is:

- A user will intentionally try to override your intent (jailbreaks, prompt injection).
- A user will accidentally paste secrets and PII.
- The model will sometimes be wrong while sounding right.
- The model will sometimes output content that is unsafe to render or act on without checks.
- If you add tools/agents, you will eventually give the system too much authority unless you actively design against it.

This aligns well with the OWASP GenAI project’s “Top 10” framing, and it also matches what you see in practice when you deploy anything that is open-ended and connected to real data.

## Mapping mitigations to the OWASP Top 10 (2025)

The OWASP GenAI Security Project maintains a 2025 Top 10 list for LLM / GenAI apps. I like it because it’s less about “prompt injection is bad” and more about the surrounding system design.

The 2025 risks are (names as listed by OWASP):

- Prompt Injection
- Sensitive Information Disclosure
- Supply Chain
- Data and Model Poisoning
- Improper Output Handling
- Excessive Agency
- System Prompt Leakage
- Vector and Embedding Weaknesses
- Misinformation
- Unbounded Consumption

I’m not going to rewrite the guide here, but the list is useful as a review checklist. If you only have time for a first pass, I would start with input/output handling, prompt leakage, and unbounded consumption because those show up immediately when real users get access.

## What I would implement (in roughly this order)

### 1) Treat prompts as data that needs policy

At minimum:

- PII/secrets detection on prompts, with redaction and/or blocking.
- Basic injection/jailbreak heuristics (not perfect, but surprisingly helpful at scale).
- Rate limits per user and per org.
- Hard caps on tokens (to avoid accidental runaway costs).

If you can only pick one “control plane” design choice, pick the one that gives you logs with stable identifiers so you can answer: who asked what, what did we send to the model, and what did the model return?

### 2) Treat model output as untrusted output

This is where “LLM apps” often fail: the output is treated as a trusted artifact and is piped straight into UI, workflows, or tools.

Examples of minimal controls that help:

- Content moderation or “allowed topics” checks for the specific product surface.
- Output validation when you expect a schema (JSON, tool-call arguments, etc.).
- Safe rendering rules (don’t blindly render raw HTML/markdown if you didn’t mean to).

### 3) Protect the system prompt like it’s a secret

If your system prompt contains policy (“never reveal X”) and it also contains product logic (“you are a support agent for Y”), leaking it is both a security issue and an IP issue.

Some gateway products describe similarity checks between user prompt/system prompt/model output, and even “canary words” that should never appear in output. Even if you don’t use those exact techniques, the broader point stands: you need detection and alarms for “the model is starting to quote internal instructions”.

### 4) If you use RAG, treat retrieval as an attack surface

RAG is where a lot of real value lives, but it’s also where you can leak sensitive context or retrieve documents that were never intended for the user.

Two principles that keep coming back:

- authorization has to happen before retrieval (or at retrieval time), not after generation,
- and you need to assume retrieved text can contain adversarial instructions (because it can).

### 5) If you use tools/agents, keep a tight leash

Agents are where “it worked in the demo” goes to die.

If the model can call external systems, you want:

- explicit allowlists for actions,
- scoped credentials,
- human approval for risky actions,
- and observability that lets you reconstruct the chain of calls later.

This is basically “excessive agency” in OWASP language.

## Vendor tools: what I look for

I’m not endorsing any specific vendor here, but if you evaluate an “AI gateway” / “AI firewall” product, I’d look for:

- policies that are easy to version and audit,
- prompt/response logging with redaction,
- support for multiple model backends,
- alerting based on both content and cost,
- and an integration path that doesn’t require a rewrite of the application.

Lakera positions Lakera Guard as a real-time security layer with policy controls and centralized monitoring, with a lot of their marketing grounded in the Gandalf ecosystem and red-teaming. That’s directionally aligned with what I think you need: a control plane that evolves faster than individual application teams can.

## References

- OWASP GenAI Security Project – LLM Top 10 (2025): https://genai.owasp.org/llm-top-10/
- F5 DevCentral – Securing the LLM User Experience with an AI Firewall: https://community.f5.com/kb/technicalarticles/securing-the-llm-user-experience-with-an-ai-firewall/330738
- Lakera Guard: https://www.lakera.ai/lakera-guard

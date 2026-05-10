---
title: "Quantum-HPC Software Stacks and the openQSE Reference Architecture: A Survey"
collection: publications
permalink: /publications/2026-04-22-openqse-reference-architecture/
excerpt: 'Quantum resources are increasingly integrated into high-performance computing and cloud environments, but quantum-HPC software stacks remain isolated, often proprietary, full-stack solutions lacking common interfaces across runtime, resource management, orchestration, and execution layers. This survey reviews nine production stacks, maps recurring design patterns and deployment choices, and identifies shared gaps in runtime abstraction, scheduling/resource management, interconnect semantics, and observability. It introduces the openQSE reference architecture with explicit layer boundaries so implementations can interoperate while preserving deployment choice and supporting both NISQ-era workloads and future FTQC systems without changing upper-layer application interfaces.'
date: 2026-04-22
venue: 'ArXiv'
paperurl: 'https://arxiv.org/abs/2604.20912'
---

This [paper](https://arxiv.org/abs/2604.20912) is available for free on the arXiv.

The work surveys production quantum-HPC software stacks and introduces the open quantum-HPC software ecosystem (openQSE) reference architecture as a way to describe layer boundaries for interoperable quantum-HPC systems.

Beyond cataloging stacks, the paper frames a practical interoperability baseline: keep application-facing interfaces stable, and separate runtime, orchestration, and execution responsibilities so sites can evolve hardware and control planes without forcing rewrites at the user layer.

The paper abstract is:
> Quantum resources are increasingly integrated into high-performance computing (HPC) and cloud environments, but quantum high-performance computing (QHPC) software stacks remain isolated, often proprietary, full-stack solutions lacking common interfaces across runtime, resource management, orchestration, and execution layers. This paper analyzes nine production QHPC stacks and identifies common design patterns and emerging requirements, covering deployment models, application interaction patterns, SDK support, and readiness for fault-tolerant operation. The survey exposes consistent needs in runtime abstraction, resource management, interconnect semantics, and observability. Based on these findings, we propose the open quantum-HPC software ecosystem (openQSE) reference architecture as a first step toward unifying the state-of-the-practice.

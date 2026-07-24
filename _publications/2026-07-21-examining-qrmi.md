---
title: "Examining QRMI as a Unified Interface for Quantum-HPC Integration"
collection: publications
permalink: /publications/2026-07-21-examining-qrmi/
excerpt: 'The Quantum Resource Management Interface (QRMI) provides a vendor-agnostic middleware layer for scheduling, executing, and monitoring quantum workloads across heterogeneous HPC environments and workload managers.'
date: 2026-07-21
venue: "ArXiv"
paperurl: 'https://arxiv.org/abs/2607.19591'
---

This [paper](https://arxiv.org/abs/2607.19591) is available for free on the arXiv.

The paper examines QRMI as a unified interface for integrating heterogeneous quantum resources into HPC environments. It extends the earlier Slurm integration to PBS, LSF, Grid Engine, Kubernetes, and Flux, comparing scheduler-specific integration patterns and alternative approaches to quantum resource management.

I contributed to the work as a Pasqal co-author and QRMI maintainer, alongside collaborators from the QRMI community.

The paper abstract is:
> The efficient and scalable integration of quantum resources into high-performance computing (HPC) environments requires standardized mechanisms for resource management, scheduling, and workflow orchestration across diverse and heterogeneous infrastructures. The Quantum Resource Management Interface (QRMI) addresses this challenge through a thin, vendor-agnostic middleware layer that provides standardized APIs for scheduling, executing, and monitoring quantum workloads while exposing quantum resources as first-class schedulable resources alongside CPUs and GPUs. This paper extends the validation of QRMI to a broad range of workload managers, including PBS, LSF, Grid Engine, Kubernetes, and the Flux Framework, encompassing traditional batch schedulers, a cloud-native orchestration platform, and a graph-based scheduler. We examine the integration patterns, implementation requirements, and scheduler-specific considerations associated with each environment and compare QRMI with alternative approaches to quantum resource integration. We demonstrate that QRMI provides a portable and flexible abstraction layer that minimizes scheduler-specific modifications while enabling consistent access to heterogeneous quantum resources across both on-premises and cloud environments.

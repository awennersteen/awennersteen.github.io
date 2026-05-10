---
title: "Integrating Quantum Processing Units into Data Center Infrastructure"
collection: publications
permalink: /publications/2026-04-14-integrating-qpus-dc-infrastructure/
excerpt: 'Quantum deployments are moving from lab environments and small private data centers toward production deployments in larger third-party data centers. This Open Compute Project white paper documents practical requirements for integrating QPUs into data center infrastructure, including facility constraints, control-plane interfaces, and operational workflows. It aligns with the OCP Data Center Integration of Quantum Information Infrastructure effort to define open specifications and interoperable practices for hybrid quantum-classical environments.'
date: 2026-04-14
venue: 'Open Compute Project white paper'
paperurl: 'https://www.opencompute.org/documents/integrating-qpus-into-dc-infrastructure-pdf'
---

This [white paper](https://www.opencompute.org/documents/integrating-qpus-into-dc-infrastructure-pdf) is available from the Open Compute Project.

It sits within OCP's Future Technologies Initiative workstream on Data Center Integration of Quantum Information Infrastructure, which focuses on open integration standards for quantum technologies in general-purpose data centers, including hardware deployment guidance and middleware directions for hybrid workflow orchestration.

The document is structured as an engineering deployment guide. It starts with a full-stack framing of quantum systems, covering logical and physical QPU layers, real-time host and interconnect needs, quantum system controllers, classical architecture concerns (AI acceleration, control-plane services, syndrome extraction, and storage), plus environmental control constraints. It then moves into practical deployment guidance: facility selection criteria, site demarcation boundaries, modality-specific installation constraints, and risk factors across facilities.

A large part of the white paper is modality-specific. It breaks out deployment considerations for neutral atoms, trapped ions, photonics, superconducting qubits, annealing systems, silicon spin qubits, and diamond-based approaches, including where facility and zone requirements diverge across technologies. The closing sections summarize future work, including non-quantum OCP project dependencies and dedicated quantum-specific efforts needed to make repeatable, scalable QPU deployments in production data center environments.

The work was authored by contributors from the National Quantum Computing Centre, Open Compute Project, D-Wave, Dell Technologies, Diraq, Fujitsu, Infleqtion, IonQ, IQM, Maybell, ORCA Computing, Oxford Quantum Circuits, Pasqal, Qblox, Quantum Brilliance, Zero Point Cryogenics, and ZPT Corp.

The paper abstract is:
> Quantum computing, communication, sensing and simulation aren't just incremental improvements to the classical ways of doing things but represents a significant paradigm shift. The datacenters needed to deploy quantum require a similar paradigm shift. Current deployments of quantum computers are typically done in bespoke environments such as lab environments, small private datacenters, etc. and not at scale in larger third party datacenters. The Open Compute Project (OCP) is actively addressing these integration hurdles through its Future Technologies Initiative (FTI), specifically within the "Data Center Integration of Quantum Information Infrastructure" workstream.

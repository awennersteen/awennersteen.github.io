---
title: "Towards a user-centric HPC-QC environment"
collection: publications
permalink: /publications/2025-11-16-user-centric-qhpc
excerpt: 'Robust execution environments are important for addressing key challenges in quantum computing, such as application development, portability, and reproducibility, and help unlock the development of modular quantum programs, driving forward hybrid quantum workflows. In this work, we show progress towards a basic, but portable, runtime environment for developing and executing hybrid quantum-classical programs running in High Performance Computing (HPC) environments enhanced with Quantum Processing Units (QPUs). The middleware includes a second layer of scheduling after the main HPC resource manager in order to improve the utilization of the QPU, and extra functionality for observability, monitoring, and admin access. This approach enables managing multiple programming Software Development Kits (SDKs) as first-class citizens in the environment by building on a recently proposed vendor-neutral Quantum Resource Management Interface (QRMI). Lastly, we discuss and show a solution for the monitoring and observability stack, completing our description of the hybrid system architecture.'
date: 2025-11-16
venue: "SC'25 workshops proceedings"
recording: "https://www.youtube.com/watch?v=DoRbE9p2LuM"
slides: "https://github.com/openQSE/Workshops/blob/main/OpenQSE-WG/openQSE-Pasqal-20260119.pdf"
paperurl: 'https://dl.acm.org/doi/10.1145/3731599.3767549'
---

The [paper](fhttps://dl.acm.org/doi/10.1145/3731599.3767549) is available for free from ACM.

It was given as a [presentation](../talks/2025-11-16-SC25) at SC25 in St. Louis, and later at the [OpenQSE meeting](/talks/2026-01-19-OpenQSE) of which there is also a recording.

This work introduces the Pasqal reference architecture for on-premise deployment of QPUs into HPC environments. We have special focus on the importance of creating a user-centric environment that is also not specific to the HPC cluster to enable users to move freely between ``execution environments" such as local emulators, cloud based QPUs and QPUs hosted by HPC centers on-premises. It builds on the previously introduced QRMI interface.

The paper abstract is:
> Robust execution environments are important for addressing key challenges in quantum computing, such as application development, portability, and reproducibility, and help unlock the development of modular quantum programs, driving forward hybrid quantum workflows. In this work, we show progress towards a basic, but portable, runtime environment for developing and executing hybrid quantum-classical programs running in High Performance Computing (HPC) environments enhanced with Quantum Processing Units (QPUs). The middleware includes a second layer of scheduling after the main HPC resource manager in order to improve the utilization of the QPU, and extra functionality for observability, monitoring, and admin access. This approach enables managing multiple programming Software Development Kits (SDKs) as first-class citizens in the environment by building on a recently proposed vendor-neutral Quantum Resource Management Interface (QRMI). Lastly, we discuss and show a solution for the monitoring and observability stack, completing our description of the hybrid system architecture.
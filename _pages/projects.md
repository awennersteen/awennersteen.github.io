---
permalink: /projects/
title: "Projects"
excerpt: "System-level integrations and selected independent systems."
layout: archive
classes: page--features
author_profile: true
description: "Selected system-level integrations across quantum and HPC, plus independent software systems, with GitHub repositories and public coverage links."
seo_image: images/awennersteen.jpg
modified: 2026-03-21
redirect_from:
  - /projects.html
---

<p>Selected projects spanning independent software systems and quantum-HPC infrastructure work.</p>

<div class="featured-cards">
  <div class="featured-cards__grid">
    <div class="feature__wrapper">
      <div class="feature__item featured-cards__card">
        <div class="archive__item">
          <span class="featured-cards__badge">FEATURED</span>
          <div class="archive__item-body">
            <h2 class="archive__item-title"><a href="#personal-projects">Personal AI Agent</a></h2>
            <div class="archive__item-excerpt">
              <p>A private assistant inspired by OpenClaw but built from scratch, connecting Telegram, OpenAI, and Google Calendar so scheduling and messaging happen from one conversational interface.</p>
            </div>
          </div>
        </div>
      </div>
      <div class="feature__item featured-cards__card">
        <div class="archive__item">
          <span class="featured-cards__badge">FEATURED</span>
          <div class="archive__item-body">
            <h2 class="archive__item-title"><a href="https://github.com/pasqal-io/qadence">Qadence</a></h2>
            <div class="archive__item-excerpt">
              <p>A digital-analog quantum SDK I originally led, focused on quantum machine learning, built on PyTorch, and designed to be fully differentiable for fast model-to-execution iteration.</p>
            </div>
            <p class="archive__item-actions">
              <a href="https://github.com/pasqal-io/qadence" class="btn btn--small">GitHub</a>
              <a href="/publications/2025-02-03-qadence/" class="btn btn--small">Publication</a>
              <a href="/talks/2024-01-20-PlanQC24-Qadence/" class="btn btn--primary btn--small">Talk</a>
            </p>
          </div>
        </div>
      </div>
      <div class="feature__item featured-cards__card">
        <div class="archive__item">
          <span class="featured-cards__badge">FEATURED</span>
          <div class="archive__item-body">
            <h2 class="archive__item-title"><a href="https://github.com/qiskit-community/qrmi">QRMI and Slurm Integration</a></h2>
            <div class="archive__item-excerpt">
              <p>Treating QPUs as first-class schedulable resources in HPC environments through vendor-neutral control-plane interfaces.</p>
            </div>
            <p class="archive__item-actions">
              <a href="https://github.com/qiskit-community/qrmi" class="btn btn--small">GitHub</a>
              <a href="https://arxiv.org/pdf/2506.10052" class="btn btn--small">Paper</a>
              <a href="/publications/2025-06-11-qrmi/" class="btn btn--primary btn--small">Details</a>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="taxonomy-chips">
  <span class="taxonomy-chips__label">Browse sections</span>
  <div class="taxonomy-chips__list">
    <a class="taxonomy-chip" href="#personal-projects">
      <span class="taxonomy-chip__name">Personal Projects</span>
    </a>
    <a class="taxonomy-chip" href="#system-level-integrations">
      <span class="taxonomy-chip__name">System-Level Integrations</span>
    </a>
  </div>
</div>

<h2 id="personal-projects" class="archive__subtitle">Personal Projects</h2>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">Personal Agent for Calendar and Messaging Automation</h2>
    <p class="archive__item-excerpt">A private assistant connecting Telegram, OpenAI, and Google Calendar endpoints in one flow. It was inspired by OpenClaw but built from scratch, and lets me schedule, reschedule, and trigger messages conversationally without switching tools.</p>
  </article>
</div>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">Intelligent Video Analytics</h2>
    <p class="archive__item-excerpt">A GPU-accelerated pipeline that detects events and extracts performance metrics directly from video streams. It cuts manual review time and makes longitudinal performance tracking much easier.</p>
  </article>
</div>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">MyConcierges</h2>
    <p class="archive__item-excerpt">A travel-tech project where we used LLMs and map data to help people plan city holidays. The product was aimed at the hospitality sector so hotels and related operators could improve their guest offering while opening new revenue channels.</p>
  </article>
</div>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">Flat Due Diligence</h2>
    <p class="archive__item-excerpt">A proptech concept using AI models to support property due diligence and generate market ideas for individual investors. The pain point came from entering the market myself and seeing how fragmented and time-consuming investor research can be.</p>
  </article>
</div>

<h2 id="system-level-integrations" class="archive__subtitle">System-Level Integrations</h2>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">QRMI (Quantum Resource Management Interface)</h2>
    <p class="archive__item-excerpt">QPUs were often treated as special-case devices in HPC operations. I helped build QRMI and the Slurm/SPANK integration path so quantum hardware can be scheduled like other shared resources. This opened a practical route for CPU-GPU-QPU workflows in real environments.</p>
    <p class="archive__item-actions">
      <a href="https://github.com/qiskit-community/qrmi" class="btn btn--small">QRMI GitHub</a>
      <a href="https://github.com/qiskit-community/spank-plugins" class="btn btn--small">SPANK GitHub</a>
      <a href="https://arxiv.org/pdf/2506.10052" class="btn btn--small">ArXiv</a>
      <a href="https://github.com/openQSE/openqse-admin/wiki/Meeting-2025-12-15" class="btn btn--small">OpenQSE Notes</a>
      <a href="/publications/2025-06-11-qrmi/" class="btn btn--primary btn--small">Details</a>
    </p>
  </article>
</div>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">CUDA-Q x Pasqal Integration (with NVIDIA)</h2>
    <p class="archive__item-excerpt">To make high-level quantum code runnable in real infrastructure, I worked on Pasqal integration pathways connected to CUDA-Q. The result is a cleaner handoff from developer code to schedulable execution on heterogeneous systems.</p>
    <p class="archive__item-actions">
      <a href="https://nvidia.github.io/cuda-quantum/latest/using/backends/hardware/neutralatom.html#pasqal" class="btn btn--small">CUDA-Q Docs</a>
      <a href="https://www.pasqal.com/newsroom/pasqal-to-advance-hybrid-quantum-computing-with-nvidia-cuda-q-platform/" class="btn btn--small">Pasqal PR (Mar 20, 2025)</a>
      <a href="https://www.pasqal.com/newsroom/pasqal-advances-hybrid-quantumai-computing-with-nvidia-nvqlink/" class="btn btn--small">Pasqal PR (Oct 28, 2025)</a>
      <a href="/talks/2025-06-13-ISC25/" class="btn btn--primary btn--small">ISC Talk</a>
    </p>
  </article>
</div>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">On-Prem QPU Deployments and Orchestration Layer</h2>
    <p class="archive__item-excerpt">Deploying QPUs in HPC centers requires more than hardware installation. I led integrations across partner sites, including CEA and JSC, and shaped the orchestration model used inside allocations so sites can enforce priorities, access classes, and runtime policies. Together, these changes made QPUs operational infrastructure for day-to-day workloads, not isolated demonstrations.</p>
    <p class="archive__item-actions">
      <a href="https://www.youtube.com/watch?v=v0u9uy1K8Aw" class="btn btn--small">OCP Recording</a>
      <a href="/talks/2025-06-13-ISC25/" class="btn btn--small">ISC Talk</a>
      <a href="/talks/2026-01-19-OpenQSE/" class="btn btn--small">OpenQSE Talk</a>
      <a href="/publications/2025-11-16-user-centric-qhpc/" class="btn btn--primary btn--small">Publication</a>
    </p>
  </article>
</div>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">Pasqal Cloud, Hybrid Execution, and HPC Emulation</h2>
    <p class="archive__item-excerpt">I worked on execution paths spanning cloud QPUs, on-prem systems, and HPC-backed emulators so teams could use the same workflow across environments. That reduced handoff friction between development and production while enabling continuous validation when hardware access was limited. The result was faster iteration, fewer environment-specific surprises, and stronger reliability before production runs.</p>
    <p class="archive__item-actions">
      <a href="/publications/2026-02-05-hybrid-algos-cloud/" class="btn btn--small">Hybrid Cloud Publication</a>
      <a href="/publications/2023-02-10-emutn/" class="btn btn--small">Emu-TN Publication</a>
      <a href="/talks/2023-09-18-IEEE-QCE23/" class="btn btn--small">IEEE QCE Talk</a>
      <a href="/talks/2026-01-19-OpenQSE/" class="btn btn--primary btn--small">OpenQSE Talk</a>
    </p>
  </article>
</div>

<div class="list__item">
  <article class="archive__item">
    <h2 class="archive__item-title">Qadence</h2>
    <p class="archive__item-excerpt">I was the original lead of Qadence, a digital-analog quantum SDK focused on quantum machine learning and practical hybrid algorithm development. Qadence is built on PyTorch and was designed as a fully differentiable framework, making gradient-based workflows first-class and tightening the loop between model design, training, and execution. Beyond shipping open-source code, it helped set the software direction for how users move from exploration to repeatable execution in Pasqal-centered workflows.</p>
    <p class="archive__item-actions">
      <a href="https://github.com/pasqal-io/qadence" class="btn btn--small">GitHub</a>
      <a href="https://arxiv.org/pdf/2401.09915" class="btn btn--small">ArXiv</a>
      <a href="/publications/2025-02-03-qadence/" class="btn btn--small">Publication</a>
      <a href="/talks/2024-01-20-PlanQC24-Qadence/" class="btn btn--primary btn--small">Talk</a>
    </p>
  </article>
</div>

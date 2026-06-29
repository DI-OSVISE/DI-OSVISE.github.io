---
layout: post
title:  "IC Power Modeling: a Systematic Literature Review"
date:   2026-06-29
---


As part of the OSVISE project, TUM and UzL performed a systematic literature
review (SLR) on integrated circuit (IC) power modeling. Following is a short
overview of our work, which has also been submitted to ACM Computing Surveys and
the preprint version is available
[here](https://github.com/DI-OSVISE/documents/blob/main/20260629-Preprint-Survey/Power-Estimation-Survey.pdf)
and [mediaTUM](https://mediatum.ub.tum.de/node?id=1857098).

Our work presents an SLR of IC power modeling research published in the past
decade. We track three co-evolving dimensions, synthesizing peer-reviewed works:
(1) Early power modeling at three abstraction levels: high-level (including
electronic system level), register transfer level (RTL), and gate-level netlist;
(2) a range of methods from deterministic analytical models to data-driven
machine learning (ML) approaches; and (3) the development of open-source
frameworks supporting power modeling.

With the rapid evolution of artificial intelligence (AI) algorithms and ML
techniques, computational power and energy demand have increased substantially.
This trend introduces new design challenges for integrated circuits (ICs).
Power-aware and energy-efficient AI accelerators have become essential for
sustainable AI development by reducing the energy consumption and environmental
footprint associated with model training and deployment. Accurate IC power
modeling is therefore a fundamental component of AI chip design. Underestimating
IC power can cause localized thermal violations and long-term reliability
degradation, whereas overestimation can lead to unnecessary energy provisioning
and reduced system efficiency. Consequently, precise power estimation is a
critical requirement in modern semiconductor design and continues to drive
innovation in IC power modeling methodologies. With the rapid evolving of AI
algorithms and ML techniques, there is a huge demand on power and energy. This
results in new design aspects of IC. Power-aware and energy efficient AI chips
have become essential for enabling sustainable AI development, as they reduce
the massive energy consumption and environmental footprint associated with
training and deploying. Therefore, IC power modeling is an essential pillar in
the AI chip design. For instance, underestimating IC power leads to localized
thermal issues and potential reliability concerns, while overestimating it
results in higher energy usage. Precise power estimation is therefore essential
in contemporary semiconductor design, driving ongoing innovation in IC power
modeling techniques. Recent years have seen numerous studies evaluating IC power
modeling for different hardware architectures and application domains. As such,
an up-to-date systematic review is needed to identify research gaps in IC power
modeling.

Our SLR identifies and highlights unresolved challenges: limited availability of
training datasets, which restricts the portability of ML-based power models;
insufficient cross-technology and cross-circuit generalization, impeding
practical adoption; and the lack of accessible open-source power models, which
hinders reproducibility and slows progress and advancement. The proposed SLR
ultimately shows that combining ML with open-source platforms can advance
robust, high-performance power models for next-generation semiconductor designs. 

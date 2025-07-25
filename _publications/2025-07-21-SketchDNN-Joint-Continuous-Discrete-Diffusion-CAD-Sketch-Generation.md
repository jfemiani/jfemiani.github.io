---
title: "SketchDNN: Joint Continuous-Discrete Diffusion for CAD Sketch Generation"
collection: publications
permalink: /publication/2025-07-21-SketchDNN-Joint-Continuous-Discrete-Diffusion-CAD-Sketch-Generation
date: 2025-07-21
venue: 'International Conference on Machine Learning (ICML)'
citation: ' Sathvik Chereddy,  John Femiani, &quot;SketchDNN: Joint Continuous-Discrete Diffusion for CAD Sketch Generation.&quot; International Conference on Machine Learning (ICML), 2025.'
---

SketchDNN is a generative model for synthesizing CAD sketches that jointly models both continuous parameters and discrete class labels through a unified continuous-discrete diffusion process. The core innovation is Gaussian-Softmax diffusion, where logits perturbed with Gaussian noise are projected onto the probability simplex via a softmax transformation, facilitating blended class modeling for high-fidelity CAD sketch generation.


[<img src="/images/SketchDNN-ICMS2025-Poster-Sathvik.png" alt="ICML 2025 Poster by Sathvik" width="400"/>](/images/SketchDNN%20Poster%20(2).pdf)

<img src="/images/SketchDNN-ICML2025-Inference-Examples-Process.png" 
    alt="Examples of the diffusion process-- random primitives are shown on the left, evolving towards realistic 2D CAD drawing exames on the right" 
    width="400"/>

## Main Points
- Mixing categorical (e.g. primitive **type**) with continuous (position, shape) information is hard, we present a novel solution.
- Without care, categories do not evolve at the right speed, preventing realistic diffusion results.
- We use a novel and **simple** representation that **actually works** to mix categorical and continuous variables
- We had to use a different *noise sechedule* and a slightly modified *inference process*
- Contrast this with autoregressive approached -- diffusion works in many passes, allowing it to respect the many symmetries and alignments (tangent features, points that should conincide). 

## Links

- **Paper:** [ArXiv](https://arxiv.org/abs/2507.11579){:target="_blank"}
- **Conference:** [ICML 2025 Virtual](https://icml.cc/virtual/2025/poster/46031){:target="_blank"}
- **Code:** [GitHub Repository](https://github.com/Sathware/SketchGNN){:target="_blank"} (code being tidied up)
- **Poster:** East Exhibition Hall A-B #E-3000 (PDF to be added later)

Use [Google Scholar](https://scholar.google.com/scholar?q=SketchDNN:+Joint+Continuous+Discrete+Diffusion+for+CAD+Sketch+Generation){:target="_blank"} for full citation

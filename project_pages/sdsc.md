---
layout: project_post
title: Signal Dice Similarity Coefficient
subtitle:  A Structure-Aware Metric for Semantic Signal Representation Learning
permalink: sdsc
authors: 
    - name: Jeyoung Lee
      url: https://ign0relee.github.io/
    - name: Hochul Kang
      url:  hhttps://cvmilab-cuk.github.io/
affiliations:
    - name: Department of Digital Media Engineering
      url:  https://mtc.catholic.ac.kr/mtc/index.do
universities:
    - name: The Catholic University of Korea
papers: sdsc
arxiv: https://arxiv.org/abs/2507.14516
github: https://github.com/CVMILab-CUK/Signal_Dice_Similarity_Coefficient
published: true
---

<figure style="text-align: center;">
    <img src="./assets/img/projects/sdsc/fig2.png" width="656" height="400" layout="responsive" alt="" class="mb3">
    <figcaption style="font-size: 14px; color: #666;">Fig. our proposed methods, a structure-aware metric function for time series elf-supervised representation learning</figcaption>
</figure>

<center>
    <h2>
        Abstract
    </h2>
</center>
<div style="max-width: 600px; margin: 0 auto; font-size:15px; text-align: justify; line-height: 1.0">
    
    We propose the Signal Dice Similarity Coefficient (SDSC), a structure-aware metric function for time series self-supervised representation learning. 

    Most Self-Supervised Learning (SSL) methods for signals commonly adopt distance-based objectives such as mean squared error (MSE), which are sensitive to amplitude, invariant to waveform polarity, and unbounded in scale. 


    These properties hinder semantic alignment and reduce interpretability. 

    SDSC addresses this by quantifying structural agreement between temporal signals based on the intersection of signed amplitudes, derived from the Dice Similarity Coefficient (DSC).


    Although SDSC is defined as a structure-aware metric, it can be used as a loss by subtracting from 1 and applying a differentiable approximation of the Heaviside function for gradient-based optimization. 


    A hybrid loss formulation is also proposed to combine SDSC with MSE, improving stability and preserving amplitude where necessary.

    Experiments on forecasting and classification benchmarks demonstrate that SDSC-based pre-training achieves comparable or improved performance over MSE, particularly in in-domain and low-resource scenarios. 

    The results suggest that structural fidelity in signal representations enhances the semantic representation quality, supporting the consideration of structure-aware metrics as viable alternatives to conventional distance-based methods.

</div>

<br/>


|||
|:---:|:---:|
|<img src="./assets/img/projects/sdsc/fig1_a.png" width="656" height="400" layout="responsive" alt="" class="mb3">| <img src="./assets/img/projects/sdsc/fig1_b.png" width="656" height="400" layout="responsive" alt="" class="mb3">|
|Inverted|Scaled|
|<img src="./assets/img/projects/sdsc/fig1_c.png" width="656" height="400" layout="responsive" alt="" class="mb3">| <img src="./assets/img/projects/sdsc/fig1_d.png" width="656" height="400" layout="responsive" alt="" class="mb3">|
|zero|noise-shifted|


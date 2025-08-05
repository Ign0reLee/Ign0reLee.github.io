---
layout: project_post
title: Signal Dice Similarity Coefficient
subtitle:  A Structure-Aware Metric for Semantic Signal Representation Learning
permalink: sdsc
authors: 
    - name: Jeyoung Lee
      url: https://ign0relee.github.io/
    - name: Hochul Kang
      url:  https://cvmilab-cuk.github.io/
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
    <figcaption style="font-size: 20px; color: #666; text-align:center; margin-top:10px;">Figure 2. our proposed methods, a structure-aware metric function for time series elf-supervised representation learning</figcaption>
</figure>

<center>
    <h2>
        Abstract
    </h2>
</center>

[LINK Drive](https://drive.google.com/drive/folders/17wDQRX8Qna1rgoLZn2-PIWH24-TB4HYb?usp=drive_link)

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


<!-- Image swiper -->
<center><h2>MSE vs SDSC Example</h2></center>
<div class="swiper mySwiper">
  <div class="swiper-wrapper">
    <div class="swiper-slide">
      <img src="./assets/img/projects/sdsc/fig1_a.png" style="width:100%;" />
      <figcaption style="14px;text-align:center; margin-top:10px; margin-bottom: 20px;">
        <em>Figure 1_a. Inverted Example <br/> Inverted : MSE=0.0200, SDSC=0.0000</em>
      </figcaption>
    </div>
    <div class="swiper-slide">
      <img src="./assets/img/projects/sdsc/fig1_b.png" style="width:100%;" />
      <figcaption style="text-align:center; margin-top:10px; margin-bottom: 20px;">
        <em>Figure 1_b. Scaled Example <br/>Scaled 0.5x : MSE=0.1249, SDSC=0.6667 <br/>Scaled  2x : MSE=0.4995, SDSC=0.6667</em>
      </figcaption>
    </div>
    <div class="swiper-slide">
      <img src="./assets/img/projects/sdsc/fig1_c.png" style="width:100%;" />
      <figcaption style="text-align:center; margin-top:10px; margin-bottom: 20px;">
        <em>Figure 1_c. Constant Zero Exmaple <br/> Zero : MSE=0.4995, SDSC=0.0000 <br/>Scaled  2x : MSE=0.4995, SDSC=0.6667</em>
      </figcaption>
    </div>
    <div class="swiper-slide">
      <img src="./assets/img/projects/sdsc/fig1_d.png" style="width:100%;" />
      <figcaption style="text-align:center; margin-top:10px; margin-bottom: 20px;">
        <em>Figure 1_c. Shifted, Noise Example<br/> Shifted &pm; 1: MSE=1.0000, SDSC=0.3887<br/> Noise : MSE=0.5062, SDSC=0.1137</em>
      </figcaption>
    </div>  
  </div>
  

  <!-- 네비게이션 버튼 -->
  <div class="swiper-button-next"></div>
  <div class="swiper-button-prev"></div>

  <!-- 페이지네이션 (dots) -->
  <div class="swiper-pagination"></div>
</div>
<p>
    Although numerically favorable, the output is structurally misaligned and functionally misleading. Such insensitivity to
    signal semantics is particularly problematic for physiological data like EEG or ECG, where subtle structural components often carry diagnostic significance. Therefore, exclusive reliance on amplitude-centric metrics may lead to semantically incorrect reconstructions.
</p>


<center>
    <h2>Definition of SDSC</h2>
</center>
<p>
    The SDSC extends DSC's concept to the signal domain by interpreting the area under the curve as
    a proxy for the waveform structure.
</p>
<center>
    $$ S(t) = E(t) \cdot R(t) $$
    $$ M(t) = \frac{ (|E(t)| + |R(t)|) - (|E(t)| - |R(t)|) }{2} $$
    $$ SDSC(E(t), R(t)) = \frac{ 2 \cdot \int  H(S(t)) \cdot M(t) \, dt }{ \int (E(t) + R(t)) \, dt} $$
</center>
<p>
    The objective in signal representation learning is
    to maximize SDSC toward 1. However, directly computing SDSC via integration is infeasible in practice, as realworld signals, such as EEG, lack known analytical expressions. 
    To address this, a discrete approximation is adopted.
</p>
<center>
    $$ SDSC(E(t), R(t)) \approx \frac{  2 \cdot \sum H(S(s)) \cdot M(s) }{ \sum (E(s) + R(s)) } $$
</center>
<p>
    Since the SDSC score is bounded in [0, 1], we can define the
    loss as 1 − SDSC(·).
</p>
<center>
    $$  \mathcal{L}_{sdsc} = 1 - SDSC(E(S), R(S)) $$
</center>

<p>
However, the use of the Heaviside step function in the SDSC introduces discontinuities, which can negatively affect the stability of training. 
To enable stable gradient-based optimization, a smooth approximation of the Heaviside function is introduced. 
The following sigmoid-based formulation is used, with a sharpness parameter &alpha;.
</p>

<center>
    $$ \hat{H}(x) = \frac{1}{1 + e^{-\alpha x}} \quad $$
    $$ SDSC(E(t), R(t)) \approx \frac{  2 \cdot \sum \hat{H}(S(s)) \cdot M(s) }{ \sum (E(s) + R(s)) }  $$
</center>

<center>
<h2>
    Live DEMO
</h2>
</center>

<!-- <iframe
	src="https://ignorelee-sdsc-demo.hf.space"
	frameborder="0"
	width="850"
	height="800"
></iframe> -->


<div style="position: relative; width: 100%; height:100%;padding-bottom: 170%;">
  <iframe src="https://ignorelee-sdsc-demo.hf.space"
          style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
          frameborder="0"
          allowfullscreen></iframe>
</div>

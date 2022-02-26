---
layout: page
title: Error-controlled DNN Interaction Detection
description: May 2021 - Present
img: assets/img/NID.gif
importance: 2
category: research
---

Despite their outstanding empirical performance, [deep neural networks (DNNs)](https://en.wikipedia.org/wiki/Deep_learning) have been mostly treated as black box models, preventing their adoption in many low-error-tolerant domains, such as healthcare, finance, robotics, and cybersecurity defense. In such contexts, interpreting DNN to reason about why certain decisions are made is crucial.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/DNN_blackbox.jpeg title: "DNN black-box" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Illustration of DNN's black-box nature<br/>
    source:
    <a href="https://bigdataforbanking.com/blog/machine-learning-without-black-boxes">
        https://bigdataforbanking.com/blog/machine-learning-without-black-boxes
    </a>
</div>

Inspired by [existing works](https://arxiv.org/pdf/1809.01185.pdf) which interpret a DNN model by selecting a subset of explanatory features subject to a controlled error rate. We are interested in detecting higher-order information captured by a DNN model, i.e., interactions between features. Modelling the fact that features often have joint effects with other features is especially useful for scientific discoveries and hypothesis validation. For example, gene-gene, gene-environment, gene-drug and gene-disease interactions are key elements in explaining genetic mechanisms in biomedical applications.

This project aims at combining a recently descibed DNN feature interaction detection algorithm ([NID](https://arxiv.org/pdf/1705.04977.pdf)) with the [knockoff filter](https://web.stanford.edu/group/candes/knockoffs/) to produce error-controled DNN interaction prediction results. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/NID_diagram.png title: "DNN architecture" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Proposed DNN architecture for error-controlled interaction detection
</div>

As shown in the diagram above, our approch invovles adding a pairwise coupling layer (inspired by [DeepPINK](https://arxiv.org/pdf/1809.01185.pdf)) to the DNN models that takes the original data and knockoff data as input. By computing the interaction scores for both original feature interacitons and knockoff feature interactions, we can use knockoff interactions as a negative control to filter out insignificant interactions and find cutoff for interaction predctions that achieves a desired False Discovery Rate (FDR).

Related Links:
- Project <a href="../../assets/pdf/interactionfdr.pdf" target="_blank">proposal</a>
- <a href="https://docs.google.com/presentation/d/12IL4a6uFFz89EPAgrQ7M0iAppqoHMpL-hY7RwWRPCcU/edit?usp=sharing" target="-blank">Slides</a> about this project
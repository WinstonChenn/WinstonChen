---
layout: page
title: Error-controlled Rankprop
description: July 2019 - Present
img: assets/img/rankprop.jpg
importance: 1
category: research
---

Rankprop is a ranking algorithm that exploits global network structure of similarity relationships among proteins in a database by performing [network propagation](https://www.nature.com/articles/nrg.2017.38) on a protein similarity network with weighted edges. It is similar to the [PageRank](https://en.wikipedia.org/wiki/PageRank) algorithm, which was the first algorithm used in Google search engine. <br/> 

{% responsive_image path: assets/img/rankprop_logo.png title: "Rankprop Logo" class: "img-fluid rounded z-depth-1" %}
More details about Rankprop can be found [here](https://rankprop.gs.washington.edu/) <br/>
Rankprop was developed for the task of protein homology detection, which usually invovles two steps:
1. Generating a high-qualitied protein similarity ranking, where the top of the ranking contains proteins that are similar to the query protein. 
2. Finds a cutoff point for positive and negative homology predictions

Rankprop effectively solved the 1st step of the problem by generating superior protein similarity rankings compared to other methods such as [BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi). For the 2nd step, there wasn't a clear solution that Rankprop or network propagation can offer. <br/>

<b>In this research project</b>, we applied the [knockoff filter](https://web.stanford.edu/group/candes/knockoffs/) to the cutoff selection of Rankprop's ranking result. Knockoff filter is statistical tool [proposed by Rina Foygel Barber and Emmanuel Candès in 2015](https://candes.su.domains/publications/downloads/FDR_regression.pdf), which controls the False Discovery Rate (FDR) in a variable selection task. 
The knockoff FDR control invovles two steps:
1. Generating a set of "knockoff variables" based on the original variables.
2. Use the knockoff variables as a negative control to identify those trully important original variables.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/rankprop_original.png title: "original variables" class: "img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/rankprop_knockoff.png title: "knockoff variables" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The idea of original variables vs. knockoff variables
</div>
More details about the knockoff filter can be found [here](https://web.stanford.edu/group/candes/knockoffs/) <br/>

In order to apply the knockoff filter on Rankprop, we proposed a novel method that generates knockoff for network data, more specifically, the protein similarity network used by Rankprop to generate ranking.<br/>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/rankprop_knockoff_gen.png title: "Knockoff Generation" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Conceptual representation of generating network knockoff
</div>

For both the original network and knockoff network, we can then generate a set of ranking, which I will call them the original ranking and the knockoff ranking. <br/>
Each protein within the original ranking would then compete with their knockoff counterpart. Those real homologies would stand out in the "competition", we can then use knockoff filter to find FDR-controlled cutoff for protein homology prediction.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% responsive_image path: assets/img/rankprop_knockoff_rank.png title: "Knockoff ranking" class: "img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Conceptual representation of generating network knockoff
</div>


Related Links:
- My [talk](https://www.youtube.com/watch?v=dZ4pvAE1OHg&t=1s) about this project at [UW's 24th Annual Undergraduate Research Symposium](https://www.washington.edu/undergradresearch/symposium/)
- <a href="../../assets/pdf/fdr_rankprop_slides.pdf" target="_blank">Slides</a> about this project
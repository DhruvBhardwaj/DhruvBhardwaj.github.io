---
layout: post
title:  "variational autoencoders"
date:   2022-10-05 16:00:22 +0530
categories: generative ai
---
{%- include mathjax.html -%}

**tl;dr** Variational Autoencoders (VAEs) are what can be called as **latent variable models**. Here, a known observation vector is transformed to a continous latent (unobserved) variable. <br>

The concept to be grasped can be seen in multiple ways. One is the *generative* idea, that a latent variable takes on a specific value and *causes* a specific value of the observed variable. Another way to see this is that of *dimensionality reduction* where an observed vector is summarized by a (latent) variable of lower dimension. <br> 

VAEs are variational because the derivation of the VAE objective involves [Calculus of Variations](https://en.wikipedia.org/wiki/Calculus_of_variations). VAEs are AutoEncoders because the final objective involves the task of reconstructing the input.<br> 

Note the relationship of VAEs with **unsupervised/self-supervised learning**, we have un-labelled data samples - and we are interested in the properties of those samples themselves (specifically the sample distribution). We want to *summarize* the samples with a latent vector, and possibly generate new samples by using new latent vectors.

[Github implementation](https://github.com/DhruvBhardwaj/variational_ae)
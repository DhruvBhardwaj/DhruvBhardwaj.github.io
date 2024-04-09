---
layout: post
title:  "image quality assessment using vision language models"
date:   2023-07-01 16:00:22 +0530
categories: image quality assessment
---
{%- include mathjax.html -%}

*This post captures details of my M.Tech. thesis work carried out from Feb 2022 to July 2023 at Indian Institute of Science, Bangalore, India. I am grateful to my supervisor Dr. Rajiv Soundararajan ([webpage](https://ece.iisc.ac.in/~rajivs/#/)), and his group at Visual Information Processing (VIP) Lab, ECE Department, IISc.*
<br>
<br>
<p>
<strong>tl;dr</strong> We learn text prompts using a self-supervised "ranking" loss, optimized in a joint vision-language space, for completely blind image quality assessment. This helps us acheive improved Blind IQA performance, irrespective of starting prompt.
</p>
Link to source code: [github]()
<br>
<br>
<h2>Introduction</h2>
<p>
Humans have an inherent sense of what constitutes a good captured image. We analyse images from multiple points-of-view, keeping the content of that image in mind. We are able to identify aesthetics of an image, as well as distortions like blur and noise(to a certain extent, as long they are preceivable). Based on this understanding, we are able to talk about image "quality".
</p>
<p>With the advent of smartphones and high-speed internet, there has been an explosion of rich multimedia content available for consumption. This includes images, and long as well as short form videos. A lot of this content is processed by automatic image processing pipelines tailored for specific applications. For example, one may require an image compression algorithm to run on images before display, to meet the demands of a low resource application. Here, it becomes important to assess if a certain automated pipeline has degraded image quality.</p>
<p>This is where Image Quality Assessment (IQA) comes in. It aims to objectively measure the quality of a distorted image in a manner that aligns with human perception. Hence, we are try to build an algorithm that looks at the same image as a human and provides a <em>score</em> to that image, which is very similar to that which would be provided by a human.</p>

<h2>About this project</h2>
<p>We specifically look at the problem of <strong>No-Reference, Opinion Unware IQA</strong>. Here, the algorithm (a deep learning based solution, for example) does not have access to a clean version of the image (No reference) at test time. It also does not know about the <em>mean opinion score (MOS)</em> of the images it has to learn from (Opinion Unaware).</p>
<p>
Additionally, we look at Multimodal Vision Language Models, which are trained on large amount of image-text data, for the IQA problem.
</p>

<h2>Method</h2>
We start with some prior work which has already shown promise in Blind-IQA by simply prompting multimodal models.
<br><br>
[CLIP-IQA](https://arxiv.org/abs/2207.12396) uses a fixed prompt pair to prompt the [CLIP]() model to score each input image for quality. For example, they suggest a prompt pair "good photo"/"bad photo" and use cosine similarity of an image representation with this pair in CLIP space to score the image. Thus for a given image $X_i$ and prompt pair $P_k, (k \in 0,1)$ encoded into their CLIP representations as $f_i=C_I(X_i)$ and $z_k=C_T(P_k), k \in \{0,1\}$, the CLIP-IQA score is given by
\begin{equation}
s_i = \frac{e^{sim_{i,1}}}{e^{sim_{i,1}}+e^{sim_{i,0}}}
\end{equation}

where $sim_{i,k}$ represents the cosine-similarity of image $i$ with prompt $k$.
<br><br>
We extend this work in the following manner
- Initially, we score an image using multiple prompt pairs (called base prompts hereafter), not just one.
- We learn continuous prompt representations in an unsupervised manner, these representations can be learnt in a manner similar to [UPL](https://arxiv.org/abs/2204.03649).
- We use a ranking based objective to order pairs or list of images drawn from the training dataset.
<br><br>
The learnable prompt representation is shared between different base prompt pairs. The number of representation vectors can be varied and appended to the beginning or end of the base prompts.
<br><br>
During training, either pairs or list of images are drawn from the dataset, and a loss is imposed on the order of scores of the images obtained in the current forward pass. The ground truth order comes from initial scores using fixed prompts.
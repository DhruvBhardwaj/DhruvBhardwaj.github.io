---
layout: post
title:  "image quality assesment using vision language models"
date:   2023-07-01 16:00:22 +0530
categories: vision language models
---

*This post captures details of my M.Tech. thesis work carried out from Feb 2022 to July 2023 at Indian Institute of Science, Bangalore, India. I am grateful to my supervisor Dr. Rajiv Soundararajan ([webpage](https://ece.iisc.ac.in/~rajivs/#/)), and his group at Visual Information Processing (VIP) Lab, ECE Department, IISc.*

<h2>Introduction</h2>
<p>
Humans have an inherent sense about what constitutes a good captured image. We analyse images from multiple point-of-view, keeping the content of that image in mind. We are able to identify aesthetics of an image, as well as distortions like blur and noise(to a certain extent, as long they are preceivable). Based on this understanding, we are able to talk about image "quality".
</p>
<p>With the advent of smartphones and high-speed internet, there has been an explosion of rich multimedia content available for consumption. This includes images, and long as well as short form videos. A lot of this content is processed by automatic image processing pipelines tailored for specific applications. For example, one may require an image compression algorithm to run on images before display, to meet the demands of a low resource application. Here, it becomes important to asses if a certain automated pipeline has degraded image quality.</p>
<p>This is where Image Quality Assesment (IQA) comes in. It aims to objectively measure the quality of a distorted image in a manner that aligns with human perception. Hence, we are try to build an algorithm that looks at the same image as a human and provides a <em>score</em> to that image, which is very similar to that which would be provided by a human.</p>

<h2>Problem setting</h2>
<p>We specifically wanted to look at the problem of <strong>No-Reference, Opinion Unware IQA</strong>. Here, the algorithm (a deep learning based solution, for example) does not have access to a clean version of the image (No reference) at test time. It also does not know about the <em>mean opinion score (MOS)</em> of the images it has to learn from. </p>
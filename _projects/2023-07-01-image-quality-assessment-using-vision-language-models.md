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
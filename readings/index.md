---
title: Readings
permalink: /readings/
---

{% for paper in site.readings %}
  <h4>
    {{ paper.title }}

    (<a style="font-size:0.95em;" href="{{ paper.url }}">summary</a> | <a style="font-size:0.95em;" href="https://github.com/DhruvBhardwaj/noise_contrastive_estimation">demo</a>)
      
  </h4>
{% endfor %}
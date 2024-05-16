---
title: Papers
permalink: /papers/
---

{% for paper in site.papers %}
  <h4>
    <a style="font-size:0.75em;" href="{{ paper.url }}">
      {{ paper.title }}
      </a>
      
  </h4>
{% endfor %}
---
layout: page
permalink: /teaching/
title: teaching
description: Academic courses that I have taught in the past.
nav: true
importance: 2
---

{% assign teaching = site.teaching | reverse %}
<ul class="cvlist">
    {% for t in teaching %}
        {% include teaching.html %}
    {% endfor %}
</ul>

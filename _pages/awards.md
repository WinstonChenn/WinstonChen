---
layout: page
permalink: /awards/
title: awards
description: List of awards I received in the past.
nav: true
importance: 3
---

{% assign awards = site.awards | reverse %}
<ul class="cvlist">
    {% for award in awards %}
        {% include awards.html %}
    {% endfor %}
</ul>

---
layout: page
permalink: /industry/
title: industry
description: My industry experience
nav: true
importance: 3
---

{% assign industry = site.industry | reverse %}
<ul class="cvlist">
    {% for i in industry %}
        {% include industry.html %}
    {% endfor %}
</ul>

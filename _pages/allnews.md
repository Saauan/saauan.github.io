---
title: "News"
layout: textlay
sitemap: false
permalink: /allnews.html
---

## News

<div class="bg-primary p-2 bg-light border rounded-3">
<!-- Nothing new yet! -->

{% for article in site.data.news %}
<b>{{ article.date }}</b>

{{ article.headline }}
{% endfor %}

</div>

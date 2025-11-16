---
title: "Posts"
layout: page
sitemap: false
permalink: /posts/
---

<ul>
  {% for post in site.posts %}
    {%- if post.hidden -%}
      {%- continue -%}
    {%- else -%}
      <li>
        {{ post.date | date_to_string }}: <a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title}}</a><br/>
        <span class="post-description">{{ post.excerpt }}</span>
      </li>
    {%- endif -%}
  {% endfor %}
</ul>

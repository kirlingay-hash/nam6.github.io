---
layout: default
title: 标签
permalink: /tags/
description: 按标签浏览粉丝之家博客文章。
---

<nav class="breadcrumbs" aria-label="面包屑">
  <a href="{{ '/' | relative_url }}">首页</a>
  <span>/</span>
  <span>标签</span>
</nav>

# 标签页

<p class="page-intro">标签用于串联跨专题的关键词，比如多平台、内容增长、GitHub Pages 和用户体验。</p>

{% if site.tags.size > 0 %}
<section class="taxonomy-links">
  {% for tag in site.tags %}
    <a class="tag-chip" href="#{{ tag[0] | url_encode }}">{{ tag[0] }} ({{ tag[1].size }})</a>
  {% endfor %}
</section>

{% for tag in site.tags %}
<section class="page-block" id="{{ tag[0] | url_encode }}">
  <h2>{{ tag[0] }}</h2>
  <div class="post-listing">
    {% for post in tag[1] %}
      {% include post-card.html post=post %}
    {% endfor %}
  </div>
</section>
{% endfor %}
{% else %}
<p>当前还没有标签内容。</p>
{% endif %}



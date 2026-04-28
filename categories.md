---
layout: default
title: 专题
permalink: /categories/
description: 按专题浏览粉丝之家博客文章。
---

<nav class="breadcrumbs" aria-label="面包屑">
  <a href="{{ '/' | relative_url }}">首页</a>
  <span>/</span>
  <span>专题</span>
</nav>

# 专题页

<p class="page-intro">按主题聚合内容，适合长期做品牌专题、内容内链和搜索收录。</p>

{% if site.categories.size > 0 %}
<section class="taxonomy-links">
  {% for category in site.categories %}
    <a class="tag-chip" href="#{{ category[0] | slugify }}">{{ category[0] }} ({{ category[1].size }})</a>
  {% endfor %}
</section>

{% for category in site.categories %}
<section class="page-block" id="{{ category[0] | slugify }}">
  <h2>{{ category[0] }}</h2>
  <div class="post-listing">
    {% for post in category[1] %}
      {% include post-card.html post=post %}
    {% endfor %}
  </div>
</section>
{% endfor %}
{% else %}
<p>当前还没有专题内容。</p>
{% endif %}

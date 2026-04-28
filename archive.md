---
layout: default
title: 归档
permalink: /archive/
description: 按时间查看粉丝之家博客的全部文章归档。
---

<nav class="breadcrumbs" aria-label="面包屑">
  <a href="{{ '/' | relative_url }}">首页</a>
  <span>/</span>
  <span>归档</span>
</nav>

# 文章归档

<p class="page-intro">这里按时间倒序展示已发布内容，方便回看，也更利于搜索引擎理解站点结构。</p>

{% if site.categories.size > 0 %}
<section class="section-header">
  <h2>按专题浏览</h2>
  <p>先看主题，再顺着时间线继续阅读。</p>
</section>
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
{% endif %}

{% if site.posts.size > 0 %}
<section class="section-header">
  <h2>按时间浏览</h2>
  <p>完整时间线保留在这里。</p>
</section>
<section class="archive-list">
{% for post in site.posts %}
  <article>
    <p class="archive-list__meta">{{ post.date | date: "%Y-%m-%d" }}</p>
    <h2><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h2>
    {% if post.description %}
    <p>{{ post.description }}</p>
    {% elsif post.excerpt %}
    <p>{{ post.excerpt | strip_html | truncate: 160 }}</p>
    {% endif %}
  </article>
{% endfor %}
</section>
{% else %}
<p>当前还没有已发布文章。</p>
{% endif %}

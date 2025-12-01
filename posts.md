---
layout: page
title: Posts
subtitle: Latest news and updates
---

## Recent Posts

{% for post in site.posts %}
<div class="post-preview{% if post.layout == 'cross-post' %} cross-post{% endif %}">
  {% if post.layout == 'cross-post' %}
    <h3><a href="{{ post.external_url }}" target="_blank">{{ post.source }}: {{ post.title }}</a></h3>
  {% else %}
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
  {% endif %}
  <p class="post-meta">Posted on {{ post.date | date: "%B %-d, %Y" }}</p>
  <div class="post-entry">
    {{ post.excerpt }}
  </div>
  {% if post.layout == 'cross-post' %}
    <a href="{{ post.external_url | relative_url }}" class="post-read-more">View on {{ post.source }}</a>
  {% else %}
    <a href="{{ post.url | relative_url }}" class="post-read-more">Read More</a>
  {% endif %}
</div>
<hr>
{% endfor %}

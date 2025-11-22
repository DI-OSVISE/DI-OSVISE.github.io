---
layout: page
title: Posts
subtitle: Latest news and updates
---

## Recent Posts

{% for post in site.posts %}
<div class="post-preview">
  <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
  <p class="post-meta">Posted on {{ post.date | date: "%B %-d, %Y" }}</p>
  <div class="post-entry">
    {{ post.excerpt }}
  </div>
  <a href="{{ post.url | relative_url }}" class="post-read-more">Read More</a>
</div>
<hr>
{% endfor %}

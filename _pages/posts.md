---
title:  "POSTS"
layout: posts
permalink: /posts/
author_profile: true
comments: false
---

{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}

{% include paginator.html %}

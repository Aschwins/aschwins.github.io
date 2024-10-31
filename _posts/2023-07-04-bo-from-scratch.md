---
layout: post
title: Bayesian Optimization From Scratch
date: 2023-07-04 08:57:00-0400
description: opening the black box of bayesian optimization
tags: data-science programming
categories: sample-posts
thumbnail: assets/img/bo-from-scratch.jpg
giscus_comments: false
related_posts: false
---

To include a jupyter notebook in a post, you can use the following code:

{% assign jupyter_path = 'assets/jupyter/bo1-BOFromScratch.ipynb' | relative_url %}
{% capture notebook_exists %}{% file_exists assets/jupyter/blog.ipynb %}{% endcapture %}
{% if notebook_exists == 'true' %}
  {% jupyter_notebook jupyter_path %}
{% else %}
  <p>Sorry, the notebook you are looking for does not exist.</p>
{% endif %}

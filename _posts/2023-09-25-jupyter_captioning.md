---
layout: post
title:  Sample Jupyter Notebook
date:   2023-09-25 00:00:00
description: Part 2 of steps to create the {old} website using Pelican and GitHub. This post shows how to use Pelican themes and plugins.
tags: pelican
categories: builds
---

{::nomarkdown}
{% assign jupyter_path = "assets/jupyter/blog.ipynb" | relative_url %}
{% capture notebook_exists %}{% file_exists assets/jupyter/blog.ipynb %}{% endcapture %}
{% if notebook_exists == "true" %}
    {% jupyter_notebook jupyter_path %}
{% else %}
    <p>Sorry, the notebook you are looking for does not exist.</p>
{% endif %}
{:/nomarkdown}
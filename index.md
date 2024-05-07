---
title: Online Hosted Instructions
permalink: index.html
layout: home
---

# Copilot Studio exercises

Links to Copilot Studio exercises on Microsoft Learn are listed below.

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %}
{% for activity in labs  %}
- [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }})
{% endfor %}

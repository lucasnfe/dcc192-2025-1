---
layout: page
title: Avisos
nav_exclude: false
description: Quadro de avisos da disciplina.
---

# Avisos

Lista completa de avisos desde o começo da disciplina:

{% assign announcements = site.announcements | reverse %}
{% for announcement in announcements %}
{{ announcement }}
{% endfor %}

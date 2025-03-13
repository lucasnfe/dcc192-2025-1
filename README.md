---
layout: home
title: DCC192 - Desenvolvimento de Jogos Digitais
nav_exclude: true
permalink: /:path/
seo:
  type: Course
  name: DCC192 - Desenvolvimento de Jogos Digitais
---

## DCC192 - Desenvolvimento de Jogos Digitais (2025/1)

Essa disciplina é uma introdução às técnicas fundamentais para a programação de jogos 2D e 3D. Os alunos são apresentados a conceitos de projeto de software, física, gráficos, inteligência artificial e áudio aplicados para o desenvolvimento de jogos. Além disso, eles utilizam ferramentas profissionais para simular um ambiente de desenvolvimento real (como um estúdio de jogos), tendo a oportunidade de publicar um portfólio pessoal com os trabalhos desenvolvidos ao longo do curso.

## Avisos

{% assign announcements = site.announcements %}
{{ announcements.last }}

## Aulas

- Segundas e Quartas, 19:00-20:40h, ICEX1017

## Professor

{% assign instructors = site.staffers | where: 'role', 'Instructor' %}
{% for staffer in instructors %}
{{ staffer }}
{% endfor %}

---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* M.Tech. in Industrial Engineering and Operations Research, IIT-Bombay, 2023
* B.Tech. in Electrical Engineering and Electronics, NIT-Calicut, 2015

Work experience
======
* NLP and LLM Researcher, TCS
  * Exploring LLM capabilities for open-ended Natural Language Generation (NLG) tasks.

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
{% if site.talks.size > 0 %}
Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
{% endif %}

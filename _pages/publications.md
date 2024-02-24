---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---


{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}

---

{% if site.author.googlescholar %}
  You can also find my articles on <u><a href="{{site.author.googlescholar}}">Google Scholar</a></u> and <u><a href="{{site.author.researchgate}}">ResearchGate</a></u> profiles.
{% endif %}
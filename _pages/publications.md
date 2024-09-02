---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

"$\alpha$-$\beta$" indicates alphabetical author order. Below is an updated list of my publications (See also [DBLP](https://dblp.org/pid/332/4208.html))



{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}

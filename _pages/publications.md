---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---
<style>
    ul.publications {
        list-style-type: none ;
        font-size: 16px ;
        margin: 5px 0px 5px 5px ;
        padding: 0px 0px 0px 0px ;
    }

    ul.publications li {
        align-items: flex-start ;
        display: flex ;
        margin: 20px 0px 20px 15px ;
        padding: 0px 0px 0px 0px ;
    }

    ul.publications li.conf {
        /* Decrement the counter by 1. */
        counter-increment: cpubs -1 ;
        /* -- */
    }

    ul.publications li.journal {
        /* Decrement the counter by 1. */
        counter-increment: jpubs -1 ;
        /* -- */
    }

    ul.publications li.preprint {
        /* Decrement the counter by 1. */
        counter-increment: ppubs -1 ;
        /* -- */
    }

    ul.publications li.conf::before {
        content: "C"counter( cpubs )"" ;
        /* -- */
        font-size: 11pt ;
        background-color: #0056b3 ;
        color: white ;
        border-radius: 5px 5px 5px 5px ;
        box-sizing: border-box ;
        margin-right: 10px ;
        min-width: 40px ;
        padding: 0px 5px 0px 5px ;
        text-align: center ;
    }

    ul.publications li.journal::before {
        content: "J"counter( jpubs )"" ;
        /* -- */
        font-size: 11pt ;
        background-color: #00B35F ;
        color: white ;
        border-radius: 5px 5px 5px 5px ;
        box-sizing: border-box ;
        margin-right: 10px ;
        min-width: 40px ;
        padding: 0px 5px 0px 5px ;
        text-align: center ;
    }

    ul.publications li.preprint::before {
        content: "W"counter( ppubs )"" ;
        /* -- */
        font-size: 11pt ;
        background-color: #d5dbdb ;
        color: #494e52;
        border-radius: 5px 5px 5px 5px ;
        box-sizing: border-box ;
        margin-right: 10px ;
        min-width: 40px ;
        padding: 0px 5px 0px 5px ;
        text-align: center ;
    }
</style>

{% assign preprintCount = 0 %}
{% assign journalCount = 0 %}
{% assign conferenceCount = 0 %}

{% for post in site.publications %}
  {% if post.preprint %}
    {% assign preprintCount = preprintCount | plus: 1 %}
  {% elsif post.journal %}
    {% assign journalCount = journalCount | plus: 1 %}
  {% else %}
    {% assign conferenceCount = conferenceCount | plus: 1 %}
  {% endif %}
{% endfor %}

<h2>Preprints</h2>
{% include base_path %}
<ul class="publications" style="counter-reset: ppubs {{ preprintCount  | plus:1 }};">
  {% for post in site.publications reversed %}
    {% if post.preprint %}
      <li class="preprint">
        {% include archive-single-publication.html %}
      </li>
    {% endif %}
  {% endfor %}
</ul>

<h2>Papers</h2>
{% include base_path %}
<ul class="publications"
    style="counter-reset: cpubs {{ conferenceCount | plus:1 }} jpubs {{ journalCount | plus:1 }};">
  {% for post in site.publications reversed %}
    {% if post.preprint %}
    {% elsif post.journal %}
      <li class="journal">
        {% include archive-single-publication.html %}
      </li>
    {% else %}
      <li class="conf">
        {% include archive-single-publication.html %}
      </li>
    {% endif %}
  {% endfor %}
</ul>

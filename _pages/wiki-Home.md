---
title: List of Super Useful Resources
permalink: /awesome-resources-useful-bookmarks/
---


<ul>
  {% for page in site.pages %}
    {% if page.title contains 'Awesome' %}
	  {% assign a = page.title | split: '-' %}
          <li><a href="{{ page.url }}">{{ a[1] }}</a></li>
    {% endif %}   <!-- resource-p -->
  {% endfor %}  <!-- page -->
</ul>

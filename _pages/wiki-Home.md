---
title: List of Super Useful Resources
permalink: /awesome-resources-useful-bookmarks/
---

# List of Awesome Useful Resources

<ul>
  {% for page in site.pages %}
    {% if page.title contains 'Awesome' %}
          <li><a href="{{ page.url }}">{{ page.title }}</a></li>
    {% endif %}   <!-- resource-p -->
  {% endfor %}  <!-- page -->
</ul>

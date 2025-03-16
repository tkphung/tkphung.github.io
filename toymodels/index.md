---
layout: default
title: Toy Models
---

# Toy Models

Here's a list of the toy models:

<ul>
    {% for model in site.toymodels_collection %}
    <li>
        <a href="{{ model.url }}">{{ model.title }}</a>
    </li>
    {% endfor %}
</ul>

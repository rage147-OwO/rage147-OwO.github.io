---
title: "U-Example"
layout: archive
permalink: categories/U-Example
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories .U-Example %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
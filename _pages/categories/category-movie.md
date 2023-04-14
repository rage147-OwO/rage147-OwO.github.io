---
title: "movie"
layout: archive
permalink: categories/movie
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.movie %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
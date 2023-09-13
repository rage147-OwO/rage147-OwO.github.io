---
title: "영화"
layout: archive
permalink: categories/영화
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.영화 %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
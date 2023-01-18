---
title: "music"
layout: archive
permalink: categories/music
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.music %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
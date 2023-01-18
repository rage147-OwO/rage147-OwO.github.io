---
title: "개인프로젝트"
layout: archive
permalink: categories/개인프로젝트
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.%ea%b0%9c%ec%9d%b8%ed%94%84%eb%a1%9c%ec%a0%9d%ed%8a%b8 %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
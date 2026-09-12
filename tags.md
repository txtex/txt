---
layout: default
title: Tags
permalink: /tags/
Tags
---

{% assign tags = site.tags | sort %}

{% for tag in tags %}

{{ tag[0] }}
<ul> {% for post in tag[1] %} <li> <a href="{{ post.url | relative_url }}">{{ post.title }}</a> <small>{{ post.date | date: "%d/%m/%Y" }}</small> </li> {% endfor %} </ul>

{% endfor %}

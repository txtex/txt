---
layout: default
title: Tags
permalink: /tags/
---

<div class="tags-page"> <span>🏷️ Tags</span>
{% assign sorted_tags = site.tags | sort %}

{% if sorted_tags.size > 0 %}

{% for tag in sorted_tags %}

  <h2 id="{{ tag[0] | slugify }}">{{ tag[0] }}</h2>

  <ul>
    {% for post in tag[1] %}
      <li>
        <a href="{{ post.url | relative_url }}">
          {{ post.title }}
        </a>
      </li>
    {% endfor %}
  </ul>

{% endfor %}

{% else %}

<p>Nenhuma tag encontrada.</p>

{% endif %}

</div>

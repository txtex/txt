---
layout: default
---
<div class="home">
{% if page.title %}
<h1 class="page-heading">{{ page.title }}</h1>
{% endif %}

{{ content }}

{% if paginator.posts.size > 0 %}

<ul class="post-list">

  {% for post in paginator.posts %}

    <li>

      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h3>

      {% if post.tags %}
        <div class="post-tags">
          🏷️
          {% for tag in post.tags %}
            <a href="{{ '/tags/' | relative_url }}#{{ tag | slugify }}">
              {{ tag }}
            </a>{% unless forloop.last %}, {% endunless %}
          {% endfor %}
        </div>
      {% endif %}

    </li>

  {% endfor %}

</ul>

{% if paginator.total_pages > 1 %}

  <div class="pager">

    {% if paginator.previous_page %}
      <a href="{{ paginator.previous_page_path | relative_url }}">
        ← Anterior
      </a>
    {% endif %}

    {% for page in (1..paginator.total_pages) %}

      {% if page == paginator.page %}

        <strong>{{ page }}</strong>

      {% elsif page == 1 %}

        <a href="{{ '/' | relative_url }}">
          {{ page }}
        </a>

      {% else %}

        <a href="{{ site.paginate_path | replace: ':num', page }}">
          {{ page }}
        </a>

      {% endif %}

    {% endfor %}

    {% if paginator.next_page %}
      <a href="{{ paginator.next_page_path | relative_url }}">
        Próxima →
      </a>
    {% endif %}

  </div>

{% endif %}

{% endif %}

</div>

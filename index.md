---
layout: default
---
{%- if page.title -%}
{{ page.title }}
{%- endif -%} {{ content }}
{% if site.paginate %} {% assign posts = paginator.posts %} {% else %} {% assign posts = site.posts %} {% endif %}

{%- if posts.size > 0 -%} {%- if page.list_title -%}

{{ page.list_title }}
{%- endif -%}
{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
{%- for post in posts -%}

<h3>
  <a class="post-link" href="{{ post.url | relative_url }}">
    {{ post.title | escape }}
  </a>
</h3>

{%- if post.tags -%}
  <div class="post-tags">
    🏷️
    {%- for tag in post.tags -%}
      <a href="{{ '/tags/' | relative_url }}#{{ tag | slugify }}">
        {{ tag }}
      </a>{% unless forloop.last %}, {% endunless %}
    {%- endfor -%}
  </div>
{%- endif -%}

{%- if site.minima.show_excerpts -%}
  {{ post.excerpt }}
{%- endif -%}
{%- endfor -%}
{% if site.paginate %}

{%- if paginator.previous_page %}
  <li>
    <a href="{{ paginator.previous_page_path | relative_url }}"
       class="previous-page"
       title="Go to Page {{ paginator.previous_page }}">
      {{ paginator.previous_page }}
    </a>
  </li>
{%- else %}
  <li><div class="pager-edge">•</div></li>
{%- endif %}

  <li>
    <div class="current-page">{{ paginator.page }}</div>
  </li>

{%- if paginator.next_page %}
  <li>
    <a href="{{ paginator.next_page_path | relative_url }}"
       class="next-page"
       title="Go to Page {{ paginator.next_page }}">
      {{ paginator.next_page }}
    </a>
  </li>
{%- else %}
  <li><div class="pager-edge">•</div></li>
{%- endif %}

</ul>
{%- endif %}
{%- endif -%}

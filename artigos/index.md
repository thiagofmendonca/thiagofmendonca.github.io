---
layout: "page"
title: "Artigos"
---

{% for post in paginator.posts %}
  <article class="archive__item">
    <h2 class="archive__item-title">
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </h2>
    <div class="archive__item-meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%d/%m/%Y" }}</time>
      {% if post.categories %}
        &nbsp;&nbsp;•&nbsp;&nbsp;
        {% for category in post.categories %}
          <a href="{{ "/categories/" | relative_url }}{{ category | slugify }}">{{ category }}</a>{% unless forloop.last %}, {% endunless %}
        {% endfor %}
      {% endif %}
      {% if post.tags %}
        &nbsp;&nbsp;•&nbsp;&nbsp;
        {% for tag in post.tags %}
          <a href="{{ "/tags/" | relative_url }}{{ tag | slugify }}">{{ tag }}</a>{% unless forloop.last %}, {% endunless %}
        {% endfor %}
      {% endif %}
    </div>
    <p class="archive__item-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
  </article>
{% endfor %}

{% include paginator.html %}

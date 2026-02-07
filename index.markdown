---
layout: default
---

<h1>Latest Posts</h1>

{% if site.posts.size > 0 %}
  <ul class="post-list">
    {% for post in site.posts %}
      <li class="post-item">
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
        {% if post.excerpt %}
          <p>{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
        {% endif %}
      </li>
    {% endfor %}
  </ul>
{% else %}
  <p>No posts yet.</p>
{% endif %}

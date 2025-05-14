---
layout: page
lang: ja
permalink: /ja/categories
title: カテゴリー
---


<div id="archives">
  {% for category in site.categories %}
    {% assign category_name = category[0] %}
    {% assign posts_in_category = category[1] %}
    {% assign filtered_posts = posts_in_category | where: "lang", page.lang %}

    {% if filtered_posts.size > 0 %}
      <div class="archive-group">
        <div id="#{{ category_name | slugify }}"></div>
        <p></p>
        
        <h3 class="category-head">{{ category_name }}</h3>
        <a name="{{ category_name | slugify }}"></a>
        <ul>
          {% for post in filtered_posts %}
            <article class="archive-item">
              <li>
                <a href="{{ site.baseurl }}{{ post.url }}">
                  {% if post.title and post.title != "" %}
                    {{ post.title }}
                  {% else %}
                    {{ post.excerpt | strip_html }}
                  {% endif %}
                </a>
              </li>
            </article>
          {% endfor %}
        </ul>
      </div>
    {% endif %}
  {% endfor %}
</div>

---
layout: page
title: カテゴリー
permalink: /categories/
---

# カテゴリー一覧

{% for category in site.categories %}
  <h2>{{ category[0] }}</h2>
  <ul>
    {% for post in category[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        <span style="color: #828282;">- {{ post.date | date: "%Y年%m月%d日" }}</span>
      </li>
    {% endfor %}
  </ul>
{% endfor %}

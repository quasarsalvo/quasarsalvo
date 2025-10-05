---
layout: page
title: 武器一覧
permalink: /categories/
---

<style>
.weapon-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 15px;
  margin: 20px 0;
}

.weapon-item {
  padding: 15px;
  background: #f5f5f5;
  border-radius: 5px;
  text-align: center;
  cursor: pointer;
  transition: background 0.3s;
}

.weapon-item:hover {
  background: #e0e0e0;
}

.weapon-item a {
  text-decoration: none;
  color: #333;
  font-weight: bold;
}

.post-list {
  margin: 10px 0;
  padding-left: 20px;
}

.post-list li {
  margin: 8px 0;
}

.category-section {
  margin-bottom: 40px;
}
</style>

# 武器一覧

{% assign categories_sorted = site.categories | sort %}
{% for category in categories_sorted %}
<div class="category-section">
  <h2 id="{{ category[0] }}">{{ category[0] }}</h2>
  <ul class="post-list">
    {% for post in category[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        <span style="color: #828282; font-size: 14px;">- {{ post.date | date: "%Y/%m/%d" }}</span>
      </li>
    {% endfor %}
  </ul>
</div>
{% endfor %}

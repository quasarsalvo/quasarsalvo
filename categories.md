---
layout: page
title: 武器一覧
permalink: /categories/
---

<script>
function showCategory(categoryName) {
  // 全て非表示
  document.querySelectorAll('.category-posts').forEach(el => {
    el.style.display = 'none';
  });
  // 選択したものだけ表示
  document.getElementById('cat-' + categoryName).style.display = 'block';
}
</script>

<style>
.weapon-list {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin: 20px 0;
}

.weapon-button {
  padding: 10px 20px;
  background: #0366d6;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.weapon-button:hover {
  background: #0256c4;
}

.category-posts {
  display: none;
  margin-top: 20px;
}
</style>


<div class="weapon-list">
{% for category in site.categories %}
  <button class="weapon-button" onclick="showCategory('{{ category[0] | slugify }}')">
    {{ category[0] }} ({{ category[1].size }})
  </button>
{% endfor %}
</div>

{% for category in site.categories %}
<div class="category-posts" id="cat-{{ category[0] | slugify }}">
  <h2>{{ category[0] }}</h2>
  <ul>
    {% for post in category[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        <span style="color: #666;">- {{ post.date | date: "%Y/%m/%d" }}</span>
      </li>
    {% endfor %}
  </ul>
</div>
{% endfor %}

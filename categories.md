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
  const target = document.getElementById('cat-' + categoryName);
  if (target) {
    target.style.display = 'block';
  }
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
  font-size: 14px;
}

.weapon-button:hover {
  background: #0256c4;
}

.category-posts {
  display: none;
  margin-top: 30px;
  padding: 20px;
  background: #f6f8fa;
  border-radius: 8px;
}

.category-posts h2 {
  margin-top: 0;
  color: #24292e;
}

.post-item {
  margin: 15px 0;
  padding: 10px 0;
  border-bottom: 1px solid #e1e4e8;
}

.post-item:last-child {
  border-bottom: none;
}

.post-date {
  color: #586069;
  font-size: 14px;
  margin-left: 10px;
}
</style>

<div class="weapon-list">
{% for category in site.categories %}
  <button class="weapon-button" onclick="showCategory('{{ category[0] }}')">
    {{ category[0] }} ({{ category[1].size }})
  </button>
{% endfor %}
</div>

{% for category in site.categories %}
<div class="category-posts" id="cat-{{ category[0] }}">
  <h2>{{ category[0] }}</h2>
  {% for post in category[1] %}
    <div class="post-item">
     <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date: "%Y/%m/%d" }}</span>
    </div>
  {% endfor %}
</div>
{% endfor %}

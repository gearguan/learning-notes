---
layout: page
title: "学习笔记"
permalink: /notes/
---

# 学习笔记

这里收录了我的所有学习笔记，按照时间和主题分类整理。

## 最新笔记

{% assign sorted_notes = site.notes | sort: 'date' | reverse %}
{% for note in sorted_notes limit:10 %}
<div class="note-item">
  <h3><a href="{{ note.url | relative_url }}">{{ note.title }}</a></h3>
  <div class="note-meta">
    <span class="note-date">{{ note.date | date: "%Y年%m月%d日" }}</span>
    {% if note.tags %}
      <span class="note-tags">
        {% for tag in note.tags %}
          <span class="tag">{{ tag }}</span>
        {% endfor %}
      </span>
    {% endif %}
  </div>
  {% if note.excerpt %}
    <p class="note-excerpt">{{ note.excerpt | strip_html | truncatewords: 30 }}</p>
  {% endif %}
</div>
{% endfor %}

## 按标签分类

{% assign all_tags = site.notes | map: 'tags' | join: ',' | split: ',' | uniq | sort %}
{% for tag in all_tags %}
  {% if tag != '' %}
### {{ tag }}
    {% assign tag_notes = site.notes | where_exp: "note", "note.tags contains tag" %}
    {% for note in tag_notes %}
- [{{ note.title }}]({{ note.url | relative_url }}) - {{ note.date | date: "%Y-%m-%d" }}
    {% endfor %}
  {% endif %}
{% endfor %}

## 所有笔记

{% for note in sorted_notes %}
- [{{ note.title }}]({{ note.url | relative_url }}) - {{ note.date | date: "%Y年%m月%d日" }}
{% endfor %}

<style>
.note-item {
  border-bottom: 1px solid #e9ecef;
  padding: 20px 0;
  margin-bottom: 20px;
}

.note-item:last-child {
  border-bottom: none;
}

.note-item h3 {
  margin: 0 0 10px 0;
}

.note-item h3 a {
  color: #2c3e50;
  text-decoration: none;
}

.note-item h3 a:hover {
  color: #007bff;
}

.note-meta {
  color: #6c757d;
  font-size: 0.9em;
  margin-bottom: 10px;
}

.note-date {
  margin-right: 15px;
}

.note-tags {
  display: inline-block;
}

.tag {
  background: #e9ecef;
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 0.8em;
  margin-right: 5px;
}

.note-excerpt {
  color: #495057;
  line-height: 1.5;
  margin: 0;
}
</style> 
---
layout: default
title: 学习笔记
permalink: /notes/
---

<div class="section">
  <a href="/" class="back-link">← 返回首页</a>
  <h1 class="section-title">💡 学习笔记</h1>
  <p class="section-desc">技术学习、新工具速览、代码片段...</p>
</div>

<div class="notes-list">
  {% for note in site.notes %}
  <a href="{{ note.url }}" class="card">
    <p class="card-meta">{{ note.date | date: "%Y-%m-%d" }}</p>
    <h3 class="card-title">{{ note.title }}</h3>
    <p class="card-excerpt">{{ note.excerpt | default: note.content | truncate: 100 }}</p>
    {% if note.tags %}
    <div class="post-tags">
      {% for tag in note.tags %}
      <span class="tag">{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}
  </a>
  {% endfor %}
</div>

{% if site.notes.size == 0 %}
<div class="empty-state">
  <p>笔记正在整理中...</p>
</div>
{% endif %}

<style>
  .back-link {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    background: var(--bg-secondary);
    border: 1px solid var(--border);
    border-radius: 8px;
    color: var(--text-secondary);
    text-decoration: none;
    font-size: 0.875rem;
    margin-bottom: 24px;
    transition: all 0.2s ease;
  }
  .back-link:hover {
    border-color: var(--accent);
    color: var(--accent);
  }
  .section-title {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 8px;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-title::before {
    content: '';
    width: 4px;
    height: 24px;
    background: linear-gradient(180deg, var(--accent) 0%, #a855f7 100%);
    border-radius: 2px;
  }
  .section-desc {
    color: var(--text-muted);
    margin-bottom: 32px;
  }
  .notes-list {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  .notes-list .card {
    display: block;
    text-decoration: none;
  }
  .empty-state {
    text-align: center;
    padding: 60px;
    color: var(--text-muted);
  }
</style>

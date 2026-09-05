---
layout: default
title: "Concept Index"
permalink: /concepts/
---

<div class="concepts-page">
  <div class="breadcrumb" style="margin-top: 1.5rem; margin-bottom: 0.5rem;">
    <a href="{{ site.baseurl }}/">Home</a> / Concepts
  </div>
  <h1 class="page-title">Concept &amp; Notation Index</h1>
  <p class="part-desc">An A–Z reference of definitions, named results, recurring proof arguments, and notation across all courses.</p>

  <!-- Filter Bar -->
  <div class="course-filter-bar" style="margin: 1.5rem 0 1rem 0; font-family: var(--sans); font-size: 0.85rem; display: flex; align-items: center; gap: 0.75rem;">
    <label for="course-filter" style="color: var(--ink-soft); font-weight: 600;">Filter by course:</label>
    <select id="course-filter" style="font-family: var(--sans); font-size: 0.85rem; padding: 0.25rem 0.5rem; border: 1px solid var(--rule); background: var(--paper); color: var(--ink);">
      <option value="all">All Courses</option>
      <option value="point-set-topology" selected>Point-Set Topology</option>
      <option value="real-analysis" disabled>Real Analysis (forthcoming)</option>
      <option value="complex-analysis" disabled>Complex Analysis (forthcoming)</option>
    </select>
  </div>

  <!-- A-Z Quick Jump -->
  {% assign letters = "A,B,C,D,E,F,G,H,I,L,M,N,O,P,Q,R,S,T,U" | split: "," %}
  <nav class="concept-letter-nav" aria-label="Alphabetical Jump">
    {% for l in letters %}
      <a href="#{{ l }}">{{ l }}</a>
    {% endfor %}
  </nav>

  <div class="concepts-container">
    {% for l in letters %}
      {% assign items_in_letter = site.data.concepts | where: "letter", l %}
      {% if items_in_letter.size > 0 %}
        <section class="concept-group" id="{{ l }}" data-course="point-set-topology">
          <h2 class="concept-letter-heading">{{ l }}</h2>
          <ul class="concept-list">
            {% for item in items_in_letter %}
              <li class="concept-item" data-course="{{ item.course }}">
                <div class="concept-title-row">
                  <span class="concept-name">{{ item.name }}</span>
                  {% if item.symbol %}<span class="concept-sym">{{ item.symbol }}</span>{% endif %}
                </div>
                <div class="concept-gloss">{{ item.gloss }}</div>
                
                {% assign published_page = nil %}
                {% for course_page in site.courses %}
                  {% if course_page.course == item.course and course_page.lecture_number == item.lecture %}
                    {% assign published_page = course_page %}
                  {% endif %}
                {% endfor %}

                <div class="concept-source">
                  {% if published_page %}
                    <a href="{{ site.baseurl }}{{ published_page.url }}{% if item.anchor %}#{{ item.anchor }}{% endif %}">{{ item.course_title }} — Lecture {{ item.lecture }}</a>
                  {% else %}
                    <span class="concept-unpub">{{ item.course_title }} — {% if item.lecture.first %}Lectures {{ item.lecture | join: ", " }}{% else %}Lecture {{ item.lecture }}{% endif %}, not yet written</span>
                  {% endif %}
                </div>
              </li>
            {% endfor %}
          </ul>
        </section>
      {% endif %}
    {% endfor %}
  </div>
</div>

<script>
(function() {
  const filter = document.getElementById('course-filter');
  if (!filter) return;
  filter.addEventListener('change', function() {
    const selected = this.value;
    const items = document.querySelectorAll('.concept-item');
    const groups = document.querySelectorAll('.concept-group');
    
    items.forEach(function(item) {
      if (selected === 'all' || item.getAttribute('data-course') === selected) {
        item.style.display = '';
      } else {
        item.style.display = 'none';
      }
    });

    groups.forEach(function(group) {
      const visible = group.querySelectorAll('.concept-item:not([style*="display: none"])');
      group.style.display = visible.length > 0 ? '' : 'none';
    });
  });
})();
</script>

---
layout: course
title: "Point-Set Topology"
subtitle: "40 lectures across four parts. Complete course archive."
course: point-set-topology
permalink: /point-set-topology/
---

This archive contains faithful, line-by-line reading notes for a 40-lecture course in point-set topology. Each lecture page maintains the lecturer's precise sequence of definitions, claims, proofs, and examples, accompanied by authored board diagrams and marked supplements.

{% assign all_lectures = site.courses | where: "course", "point-set-topology" | where_exp: "item", "item.lecture_number != nil" %}
{% assign drafted_count = all_lectures | where: "status", "drafted" | size %}
{% assign verified_count = all_lectures | where: "status", "verified" | size %}
<div class="course-progress-summary">
  Course Progress: <strong>{{ drafted_count }} drafted</strong>, <strong>{{ verified_count }} verified</strong> (of 40 lectures).
</div>

---

<section class="part-section">
  <h2 class="part-header">Part I: Building Spaces (Lectures 1–6)</h2>
  <p class="part-desc">Topological spaces and how to build them: definitions, standard topologies, bases, subspace and product topologies.</p>
  
  <ul class="lecture-accordion">
    {% assign part1_lectures = site.courses | where: "course", "point-set-topology" | where_exp: "item", "item.lecture_number >= 1" | where_exp: "item", "item.lecture_number <= 6" | sort: "lecture_number" %}
    {% for lecture in part1_lectures %}
      <li class="lecture-row">
        <details>
          <summary>
            <a href="{{ site.baseurl }}{{ lecture.url }}" class="lecture-row-title">Lecture {{ lecture.lecture_number }}: {{ lecture.title }}</a>
            {% if lecture.status %}
              <span class="status-badge {{ lecture.status }}">{{ lecture.status }}</span>
            {% endif %}
          </summary>
          <div class="lecture-row-coverage">{{ lecture.coverage }}</div>
          <div class="lecture-row-meta">
            <span>{{ lecture.figures | default: 0 }} figure{% if lecture.figures != 1 %}s{% endif %}</span>
            <span>·</span>
            <span>{{ lecture.corrections | default: 0 }} correction{% if lecture.corrections != 1 %}s{% endif %}</span>
          </div>
        </details>
      </li>
    {% else %}
      <li class="empty-list-note">No lectures published yet.</li>
    {% endfor %}
  </ul>
</section>

<section class="part-section">
  <h2 class="part-header">Part II: Continuous Maps and Metric Spaces (Lectures 7–15)</h2>
  <p class="part-desc">Continuous maps, closed sets, metric spaces: preimages, homeomorphisms, metric topology, sequential convergence.</p>
  
  <ul class="lecture-accordion">
    {% assign part2_lectures = site.courses | where: "course", "point-set-topology" | where_exp: "item", "item.lecture_number >= 7" | where_exp: "item", "item.lecture_number <= 15" | sort: "lecture_number" %}
    {% for lecture in part2_lectures %}
      <li class="lecture-row">
        <details>
          <summary>
            <a href="{{ site.baseurl }}{{ lecture.url }}" class="lecture-row-title">Lecture {{ lecture.lecture_number }}: {{ lecture.title }}</a>
            {% if lecture.status %}
              <span class="status-badge {{ lecture.status }}">{{ lecture.status }}</span>
            {% endif %}
          </summary>
          <div class="lecture-row-coverage">{{ lecture.coverage }}</div>
          <div class="lecture-row-meta">
            <span>{{ lecture.figures | default: 0 }} figure{% if lecture.figures != 1 %}s{% endif %}</span>
            <span>·</span>
            <span>{{ lecture.corrections | default: 0 }} correction{% if lecture.corrections != 1 %}s{% endif %}</span>
          </div>
        </details>
      </li>
    {% else %}
      <li class="empty-list-note">No lectures published yet.</li>
    {% endfor %}
  </ul>
</section>

<section class="part-section">
  <h2 class="part-header">Part III: Connectedness (Lectures 16–22)</h2>
  <p class="part-desc">Connectedness and path connectedness: connected components, path components, matrix groups, topological counterexamples.</p>
  
  <ul class="lecture-accordion">
    {% assign part3_lectures = site.courses | where: "course", "point-set-topology" | where_exp: "item", "item.lecture_number >= 16" | where_exp: "item", "item.lecture_number <= 22" | sort: "lecture_number" %}
    {% for lecture in part3_lectures %}
      <li class="lecture-row">
        <details>
          <summary>
            <a href="{{ site.baseurl }}{{ lecture.url }}" class="lecture-row-title">Lecture {{ lecture.lecture_number }}: {{ lecture.title }}</a>
            {% if lecture.status %}
              <span class="status-badge {{ lecture.status }}">{{ lecture.status }}</span>
            {% endif %}
          </summary>
          <div class="lecture-row-coverage">{{ lecture.coverage }}</div>
          <div class="lecture-row-meta">
            <span>{{ lecture.figures | default: 0 }} figure{% if lecture.figures != 1 %}s{% endif %}</span>
            <span>·</span>
            <span>{{ lecture.corrections | default: 0 }} correction{% if lecture.corrections != 1 %}s{% endif %}</span>
          </div>
        </details>
      </li>
    {% else %}
      <li class="empty-list-note">No lectures published yet.</li>
    {% endfor %}
  </ul>
</section>

<section class="part-section">
  <h2 class="part-header">Part IV: Compactness, Quotients, Separation (Lectures 23–40)</h2>
  <p class="part-desc">Compactness, quotients, and separation: Hausdorff spaces, Heine–Borel, one-point compactifications, quotient groups, Urysohn's lemma, Tietze extension theorem, Urysohn metrization.</p>
  
  <ul class="lecture-accordion">
    {% assign part4_lectures = site.courses | where: "course", "point-set-topology" | where_exp: "item", "item.lecture_number >= 23" | where_exp: "item", "item.lecture_number <= 40" | sort: "lecture_number" %}
    {% for lecture in part4_lectures %}
      <li class="lecture-row">
        <details>
          <summary>
            <a href="{{ site.baseurl }}{{ lecture.url }}" class="lecture-row-title">Lecture {{ lecture.lecture_number }}: {{ lecture.title }}</a>
            {% if lecture.status %}
              <span class="status-badge {{ lecture.status }}">{{ lecture.status }}</span>
            {% endif %}
          </summary>
          <div class="lecture-row-coverage">{{ lecture.coverage }}</div>
          <div class="lecture-row-meta">
            <span>{{ lecture.figures | default: 0 }} figure{% if lecture.figures != 1 %}s{% endif %}</span>
            <span>·</span>
            <span>{{ lecture.corrections | default: 0 }} correction{% if lecture.corrections != 1 %}s{% endif %}</span>
          </div>
        </details>
      </li>
    {% else %}
      <li class="empty-list-note">No lectures published yet.</li>
    {% endfor %}
  </ul>
</section>

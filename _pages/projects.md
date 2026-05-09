---
layout: page
title: Projects
permalink: /projects/
# description: A growing collection of your cool projects.
nav: true
nav_order: 3
# display_categories: [work, fun]
horizontal: true
---

<!-- pages/projects.md -->
<div class="projects">
<style>
.projects .projects-list { list-style: none; padding: 0; margin: 0; }
.projects .projects-list li { display: flex; align-items: center; gap: 1rem; padding: .5rem .75rem; border-bottom: 1px solid #eee; }
.projects .projects-list li:last-child { border-bottom: none; }
.projects .projects-list img.thumb { width: 72px; height: 48px; object-fit: cover; border-radius: 4px; flex: 0 0 auto; }
.projects .project-info { flex: 1 1 auto; min-width: 0; }
.projects .project-title { margin: 0 0 .25rem 0; font-size: 1rem; font-weight: 600; }
.projects .project-desc { margin: 0; color: #666; font-size: .9rem; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.projects .project-meta { font-size: .8rem; color: #999; }
</style>
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  <ul class="projects-list">
    {% for project in sorted_projects %}
    <li>
      {% if project.image %}
      <a href="{{ project.url | relative_url }}"><img class="thumb" src="{{ project.image }}" alt="{{ project.title }} thumbnail"></a>
      {% endif %}
      <div class="project-info">
        <a href="{{ project.url | relative_url }}"><h3 class="project-title">{{ project.title }}</h3></a>
        <p class="project-desc">{{ project.excerpt | default: project.description }}</p>
        {% if project.date or project.technologies %}
        <div class="project-meta">{% if project.date %}{{ project.date | date: "%Y" }}{% endif %}{% if project.technologies %} • {{ project.technologies | join: ", " }}{% endif %}</div>
        {% endif %}
      </div>
    </li>
    {% endfor %}
  </ul>
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% comment %} List-style layout with thumbnail and narrow rows {% endcomment %}
  <ul class="projects-list">
    {% for project in sorted_projects %}
    <li>
      {% if project.image %}
      <a href="{{ project.url | relative_url }}"><img class="thumb" src="{{ project.image }}" alt="{{ project.title }} thumbnail"></a>
      {% endif %}
      <div class="project-info">
        <a href="{{ project.url | relative_url }}"><h3 class="project-title">{{ project.title }}</h3></a>
        <p class="project-desc">{{ project.excerpt | default: project.description }}</p>
        {% if project.date or project.technologies %}
        <div class="project-meta">{% if project.date %}{{ project.date | date: "%Y" }}{% endif %}{% if project.technologies %} • {{ project.technologies | join: ", " }}{% endif %}</div>
        {% endif %}
      </div>
    </li>
    {% endfor %}
  </ul>
{% endif %}
</div>

---
layout: page
title: projects
permalink: /projects/
description: Selected projects in systems, hardware, trading, robotics, and practice.
nav: true
nav_order: 2
display_categories: [systems, hardware, trading, robotics, practice]
horizontal: false
---

What I've been working on:

- Learning compilers and building a C [compiler](https://github.com/WilliamZhang20/c-compiler) in Rust.
- Building a custom [AI chip](https://github.com/WilliamZhang20/ECE298A-TPU) on Tiny Tapeout in Verilog and Python, with a custom PyTorch compiler.
- Developing an algorithmic stock and options [trader](https://github.com/WilliamZhang20/cvx-trader) using [CVXPY](https://www.cvxpy.org/).
- Working through [LeetCode](https://leetcode.com/u/WilliamZhang20/), with 440+ solved problems and a growing focus on design problems.

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>

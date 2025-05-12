---
layout: page
title: The Garden of Forking Paths
permalink: /:path/
description: "Landing page. Summary of content."
nav_order: 1
has_children: false
has_toc: false
---
>“I thought of a labyrinth of labyrinths, of one sinuous spreading labyrinth that would encompass the past and the future and in some way involve the stars.” 
― Jorge Luis Borges, The Garden of Forking Paths

These pages contain notes and references on random topics that I try to think about beyond my physics. It covers mostly books, art and films. I will also use this space to record some of my writings but the main goal is to capture my thoughts.

<div>
  <h2>Topics by Subject</h2>
  <ul>
    {% assign all_tags = "" | split: "," %}

    {% for entry in site.pages %}
      {% unless entry.url contains '.json' or entry.url contains '.csv' or entry.url contains '.css' or entry.url contains '.txt' or entry.url contains 'home' or entry.url contains 'tuffo' or entry.url contains 'marmellata' or entry.url contains 'jam' %}
        {% assign current_tags = entry.tags %}
        {% if current_tags %}
          {% assign all_tags = all_tags | concat: current_tags %}
        {% endif %}
      {% endunless %}
    {% endfor %}

    {% assign sorted_tags = all_tags | uniq | sort %}
    {% assign total_tags = sorted_tags | size %}
    {% assign half_tags = total_tags | divided_by: 2 %}

    <div style="float: left; width: 50%;">
      {% for tag in sorted_tags offset: half_tags %}
        <h3>{{ tag }}</h3>
        <ul>
          {% assign sorted_pages = site.pages | sort: 'title' %}
          {% for page in sorted_pages %}
            {% unless page.url contains '.json' or page.url contains '.csv' or page.url contains '.css' or page.url contains '.txt' or page.url contains 'home' or page.url contains 'tuffo' or page.url contains 'marmellata' or page.url contains 'jam' %}
              {% if page.tags contains tag %}
                <li>
                  <a href="{{page.url }}">{{ page.title }}</a>
                </li>
              {% endif %}
            {% endunless %}
          {% endfor %}
        </ul>
      {% endfor %}
    </div>

    <div style="float: left; width: 50%;">
      {% for tag in sorted_tags limit: half_tags %}
        <h3>{{ tag }}</h3>
        <ul>
          {% assign sorted_pages = site.pages | sort: 'title' %}
          {% for page in sorted_pages %}
            {% unless page.url contains '.json' or page.url contains '.csv' or page.url contains '.css' or page.url contains '.txt' or page.url contains 'home' or page.url contains 'tuffo' or page.url contains 'marmellata' or page.url contains 'jam' %}
              {% if page.tags contains tag %}
                <li>
                  <a href="{{ "/xthphys" | append: page.url }}">{{ page.title }}</a>
                </li>
              {% endif %}
            {% endunless %}
          {% endfor %}
        </ul>
      {% endfor %}
    </div>

  </ul>
</div>



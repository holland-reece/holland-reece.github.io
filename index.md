---
title: Holland Reece Brown
layout: default
---

# Data Engineer | ML Systems, ETL, & Scalable Data Pipelines | SQL • Python • Airflow • Cloud • Analytics
Data Engineer with 3+ years of experience designing _scalable ETL pipelines_ and __designing hybrid on-premises/cloud data 
infrastructure__. Skilled in __Python, SQL, Airflow, dbt, cloud platforms (GCP, AWS, Azure)__. 

## About Me

## Recent Blog Posts

{% assign recent_posts = site.posts | where_exp: "p", "p.draft != true" | slice: 0, 3 %}

<div class="post-cards">
  {% for post in recent_posts %}
  <a class="post-card" href="{{ post.url | relative_url }}">
    <div class="thumb"
         style="background-image:url('{{ post.thumbnail | default: "/assets/images/default-thumb.jpg" | relative_url }}');">
    </div>
    <div class="meta">
      <h3>{{ post.title }}</h3>
      <p class="date">{{ post.date | date: "%b %-d, %Y" }}</p>
      <p class="excerpt">{{ post.excerpt | strip_html | truncate: 110 }}</p>
    </div>
  </a>
  {% endfor %}
</div>

<p class="more">
  <a class="btn"
        href="{{ "/blog" | relative_url }}"
        style="background-color:#ff6600; border-color:#958FCF; color:#958FCF;">
    View all posts →
  </a>
</p>

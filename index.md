---
title: Holland Reece Brown
layout: default
---

<div class="banner-profile">
  <img src="/assets/images/profile_pic.jpeg" alt="Profile picture" class="profile-pic">
</div>

## Intro
My name is Holland and I'm a data engineer/analyst with experience in hybrid cloud/on-prem infra, platform engineering, ML Ops, statistical data analysis and data visualization in medical research. I'm looking for opportunities to apply my skills in the private sector. I'll be posting about my ongoing projects and current events in data engineering [here](https://holland-reece.github.io/blog.html). If you'd like to know more about me, you can look [here](https://holland-reece.github.io/about_me.html).

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
        style="background-color:#FFFFFF; border-color:#958FCF; color:#958FCF;">
    View all posts →
  </a>
</p>

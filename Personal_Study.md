---
layout: page
title: Personal Study
permalink: /Personal_Study/
---


<h3>Post List</h3><br /><br />

개인적으로 공부하거나, 세미나에 사용한 자료, 정리한 자료등을 모아 놓는 포스트들 입니다.

<ul>
  {% for post in site.tags."PersonalStudy" %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
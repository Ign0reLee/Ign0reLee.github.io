---
layout: page
title: Translation
permalink: /translation/
---

  이곳은 번역글과 관련된 칼럼을 모아놓은 곳입니다.

  번역은 항상 원 저작자의 허락을 받은 후 게시할 예정입니다.

<h3>Post List</h3><br /><br />

<ul>
  {% for post in site.tags."translation" %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
---
layout: page
title: Contact
permalink: /contact/
---


<h1>Contact List</h1><br /><br />

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
---
layout: page 
title: Coding, more coding!
tagline: By 夜鸣剑
---
{% include JB/setup %}

{% for post in site.posts %}
<div class = "card">
  <h2>  {{ post.title }} </h2>
  {{ post.content  | | split:'<!--break-->' | first }}
<div class = "read_more">
  Written on {{ post.date | date:"%d/%m/%Y" }}.
  <a class="fa fa-link" href="{{ BASE_PATH }}{{ post.url }}"> Read more&hellip;</a>
</div>
</div>
<br>
{% endfor %}


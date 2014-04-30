---
layout: page
title: Modeling My Simple Life
subtitle: hello
keywords: economics, R, LaTeX, travel, NBA, football  
author: ryanlhxu
isIndex: true
---
{% include JB/setup %}

![The Tibet]({{ site.url }}/assets/tibet.jpg)

什么时候才能去西藏呢。。。

先放张图激励一下自己。

## My Blog
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## Contact
* Weibo: [@不理不睬Ryan](http://weibo.com/economicgay)
* Email: [ryanlhxu@gmail.com](mailto:ryanlhxu@gmail.com)


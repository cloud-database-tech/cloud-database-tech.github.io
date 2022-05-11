---
layout: default
title: 首页
---
该GitHub Pages用于"云数据库技术-行业动态"的内容归档，大部分时候双周更新一次，可以通过如下公众号订阅：云数据库技术

![云数据库技术](https://cloud-database-tech.github.io/images/qrcode.jpg)

同时，可以通过该仓库的Issue提交希望展示的内容。

归档：


<ul>

{% assign thepages = site.pages | sort: 'my_title' | reverse %} 

{% for page in thepages %}
  {% if page.categories contains 'updating' %}
    <li>
    <a href="{{ page.url }}">{{page.my_title}}</a>
    </li>
  {% endif %}
{% endfor %}
</ul>

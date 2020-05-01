---
layout: default
title: Master Data Science by Kien Tran
---
# {{ page.title }}

{% for post in site.posts %}

### {{ post.date | date_to_string }} » [{{ post.title }}]({{ post.url }})
> {{ post.excerpt }}

{% endfor %}
---
layout: page
title: Hello World!
tagline: Supporting tagline
---
{% include JB/setup %}

# This website is a work in progress
Since my webhost had *another* failure, I just moved to something else.

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

* Proper About page
* import some of the old stuff
* stuff
* more stuff
* Theme



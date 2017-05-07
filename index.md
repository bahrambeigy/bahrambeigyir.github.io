---
layout: page
title: Hello World!
tagline: Yeah!
---
{% include JB/setup %}


    
## Welcome!

Dear visitors, I will try to add some content to this `hello world` post.

    $ Some cool coding stuff :)


Other Posts:

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

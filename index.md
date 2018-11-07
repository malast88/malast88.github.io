---
layout: home
---
# Stanislavs Malahvejs personal site

This is just a simple personal site and blog to track my progress in learning, collect useful links and thoughts.

# About me

[Achievements and certificates](achievements.md)

# Posts
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.date | date_to_long_string }}: {{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
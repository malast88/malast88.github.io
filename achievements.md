---
layout: page
title: Achievements and achievementificates
---
# List of achievements and certificates
<link rel="stylesheet" href="assets/style.css">
<table>
  <tr>
    <th>Date</th>
    <th>Issuer</th>
    <th>Title</th>
    <th>Files</th>
  </tr>
{% for achievement in site.data.achievements %}
  <tr>
    <td>{{ achievement.date }}</td>
    <td>
      {% if achievement.issuer.url != null %}
        <a href="{{ achievement.issuer.url }}">{{ achievement.issuer.title }}</a>
      {% else %}
        {{ achievement.issuer.title }}
      {% endif %}
	</td>
    <td>
      {% if achievement.url != null %}
        <a href="{{ achievement.url }}">{{ achievement.title }}</a>
      {% else %}
        {{ achievement.title }}
      {% endif %}
  </td>
    <td>
      <a href="{{ achievement.filePNG }}">
	    <img 
		class="thumbnail-img"
	    src="{{ achievement.thumbnail.url }}" 
		alt="Click for the full size"
		title="Click for the full size"
		{% if achievement.thumbnail.width != null %}width="{{ achievement.thumbnail.width }}"{% endif %}
		{% if achievement.thumbnail.height != null %}height="{{ achievement.thumbnail.height }}"{% endif %}/>
	  </a>
    <br/>
    {% if achievement.fileOriginal != null %}
      <a href="{{ achievement.fileOriginal.url }}">Original ({{ achievement.fileOriginal.type }})</a>
    {% endif %}
  </td>
  </tr>
{% endfor %}
</table>
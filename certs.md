---
layout: page
title: Achievements and certificates
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
{% for cert in site.data.certs %}
  <tr>
    <td>{{ cert.date }}</td>
    <td>
      {% if cert.issuer.url != null %}
        <a href="{{ cert.issuer.url }}">{{ cert.issuer.title }}</a>
      {% else %}
        {{ cert.issuer.title }}
      {% endif %}
	</td>
    <td>
      {% if cert.url != null %}
        <a href="{{ cert.url }}">{{ cert.title }}</a>
      {% else %}
        {{ cert.title }}
      {% endif %}
  </td>
    <td>
      <a href="{{ cert.filePNG }}">
	    <img 
		class="thumbnail-img"
	    src="{{ cert.thumbnail.url }}" 
		alt="Click for the full size"
		title="Click for the full size"
		{% if cert.thumbnail.width != null %}width="{{ cert.thumbnail.width }}"{% endif %}
		{% if cert.thumbnail.height != null %}height="{{ cert.thumbnail.height }}"{% endif %}/>
	  </a>
    <br/>
    {% if cert.fileOriginal != null %}
      <a href="{{ cert.fileOriginal.url }}">Original ({{ cert.fileOriginal.type }})</a>
    {% endif %}
  </td>
  </tr>
{% endfor %}
</table>
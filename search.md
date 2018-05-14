---
title: Search
layout: default
updated: 14 May 2018
---
<form action="{{ site.baseurl }}/search/" method="get">
  <label for="search-box">Search</label>
  <input type="text" id="search-box" name="query">
  <input type="submit" value="search">
</form>

<ul id="search-results"></ul>

<script>
  window.store = {
  	{% for page in site.pages %}
	  "{{ page.url | slugify }}": {
        "title": "{{ page.title | xml_escape }}",
        "group": "{{ page.group | xml_escape }}",
        "content": {{ page.content | strip_html | strip_newlines | jsonify }},
        "url": "{{ page.url | xml_escape }}"
      }
      {% unless forloop.last %},{% endunless %}
  	{% endfor %}
  };
</script>
<script src="{{ site.baseurl }}/js/lunr.js"></script>
<script src="{{ site.baseurl }}/js/search.js"></script>

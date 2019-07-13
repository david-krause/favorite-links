[HTML FILE](https://david-krause.github.io/favorite-links/favorites.html)


<ul>
	{% for post in site.posts %}
		<li><a href="{{ site.url }}/{{site.title}}{{ post.url }}">{{ post.date | date_to_string }} {{ post.title }}</a></li>
	{% endfor %}
</ul>

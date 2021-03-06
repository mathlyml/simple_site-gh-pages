---
layout: page
title: "The Legend of Hua Mulan: 1,500 Years of History | Mulanbook"
description: "Learn about the real history behind the legend of Mulan from both ancient and modern texts, read the original Hua Mulan novels, and discover the truth behind one of the most fascinating Chinese legends."
---

{::nomarkdown}

{% assign dynastyArr = "overview#northern-wei#tang#yuan#ming#qing#post-imperial" | split: '#' %}
{% assign dynastyNames = "Overview#Northern Wei (386&ndash;534 AD)#Tang Dynasty (618&ndash;907 AD)#Yuan Dynasty (1271&ndash;1368 AD)#Ming Dynasty (1368&ndash;1644 AD)#Qing Dynasty (1644&ndash;1912)#Post-Imperial China (1912&ndash;Present)" | split: '#' %}
{% assign dynastyAlts = "Overview#A relic from the Northern Wei dynasty. Image source: http://bit.ly/2GuB2Vv#A pagoda built during the Tang Dynasty. Image source: http://bit.ly/2GpfHwP#A tower built durnig the Yuan Dynasty. Image source: http://bit.ly/2LIJlkX#An arch constructed during the Ming Dynasty. Image source: http://bit.ly/2GveIuU#A gate to the Forbidden City, which was used during the Qing Dynasty. Image source: http://bit.ly/2ybwq23#National government office of the ROC. Image source: http://bit.ly/2yNrPTX" | split: '#' %}


{% assign imageCount = 0 %}
{% for dynasty in dynastyArr %}
	{% if dynasty != "overview" %}
		<h4 class="heading text-left mb-5"><img data-src="/assets/images/thumbs/dynasties/{{ dynasty }}.jpg" width="80" height="80" class="lazy" alt="{{ dynastyAlts[forloop.index0] }}" /><a name="{{ dynasty }}">{{ dynastyNames[forloop.index0] }}</a></h4>
	{% endif %}

	{% assign folderName = '/' | append: dynasty | append: '/' %}
	{% assign folder = site.pages | where_exp: "item" , "item.path contains folderName" | sort: "num" %}

	{% for article in folder %}
	{% if article.layout == "post" %}
		<div class="row {% if forloop.last %} last_article {% else %} first_article {% endif %}">
			<div class="col-md-4 main-1">
				{% if article.image contains "#" %}
					{% assign imageArr = article.image | split: '#' %}
					{% assign defaultImage = imageArr[0]  %}
				{% else %}
					{% assign defaultImage = article.image  %}
				{% endif %}

				<a href="{% if article.overrideurl %}{{ article.overrideurl }}{% else %}{{ article.url }}{% endif %}"><img src="/assets/images/thumbs/articles/placeholder.png" data-src="/assets/images/thumbs/articles/{{ defaultImage }}" style="background-color: #{{ article.bg }}" class="lazy img-fluid" /></a>
				{% assign imageCount = imageCount | plus:1 %}
			</div>
			<div class="col-md-8 main-2">
				<h3 class="mt-2"><a href="{% if article.overrideurl %}{{ article.overrideurl }}{% else %}{{ article.url }}{% endif %}">{{ article.title }}</a></h3>
				<p class="mt-3">{{ article.description }}</p>
			</div>
		</div>
	{% endif %}
	{% endfor %}
{% endfor %}

<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/vanilla-lazyload@12.0.0/dist/lazyload.min.js" onload="var lazyLoadInstance=new LazyLoad({elements_selector:'.lazy'});"></script>
{:/}

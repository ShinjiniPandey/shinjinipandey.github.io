---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

A list of all the posts and pages found on the site. You can also take a look at the [XML version]({{ base_path }}/sitemap.xml) instead.


<h2>Pages</h2>
{% for post in site.pages %}
  {% include archive-single.html %}
{% endfor %}

<div class="list__item">
  <article class="archive__item" itemscope="" itemtype="http://schema.org/CreativeWork">
    

    <h2 class="archive__item-title" itemprop="headline">
      
        <a href="http://localhost:4000/pub.html" rel="permalink">Research</a>
      
    </h2>

  </article>
</div>


<div class="list__item">
  <article class="archive__item" itemscope="" itemtype="http://schema.org/CreativeWork">
    

    <h2 class="archive__item-title" itemprop="headline">
      
        <a href="http://localhost:4000/resume" rel="permalink">CV</a>
      
    </h2>

  </article>
</div>

<!---
<h2>Posts</h2>
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}
-->

{% capture written_label %}'None'{% endcapture %}

<!---
{% for collection in site.collections %}
{% unless collection.output == false or collection.label == "posts" %}
  {% capture label %}{{ collection.label }}{% endcapture %}
  {% if label != written_label %}
  <h2>{{ label }}</h2>
  {% capture written_label %}{{ label }}{% endcapture %}
  {% endif %}
{% endunless %}
{% for post in collection.docs %}
  {% unless collection.output == false or collection.label == "posts" %}
  {% include archive-single.html %}
  {% endunless %}
{% endfor %}
{% endfor %}
-->


---
layout: page
title: "Cozy Cafe in Seoul"
date: 2024-02-03
thumbnail: /assets/images/life/cafe/thumbnail.jpg
images:
  - /assets/images/life/cafe/exterior.jpg
  - /assets/images/life/cafe/coffee.jpg
  - /assets/images/life/cafe/interior.jpg
  - /assets/images/life/cafe/dessert.jpg
---

<div class="life-post-header mb-4">
  <p class="text-muted">{{ page.date | date: "%B %d, %Y" }}</p>
</div>

<!-- Image Carousel -->
{% if page.images %}
<div class="mb-4">
  {% capture carousel_images %}{% for image in page.images %}{{ image }}
{% endfor %}{% endcapture %}
  {% assign post_id = page.path | split: "/" | last | split: "." | first %}
  {% include elements/carousel.html carousel_id="life-{{ post_id }}" carousel_images=carousel_images %}
</div>
{% endif %}

Discovered this amazing little cafe in Hongdae today! ☕

The atmosphere was perfect for studying and the coffee was exceptional. They roast their own beans and you can really taste the difference.

Spent the afternoon working on my projects while enjoying their signature latte and homemade cheesecake. The barista was super friendly and even shared some tips about coffee brewing.

Definitely adding this to my list of favorite study spots in Seoul!

<!-- Back to Life button -->
<div class="mt-4">
  <a href="/life/" class="btn btn-outline-primary">
    <i class="fas fa-arrow-left"></i> Back to Life
  </a>
</div>

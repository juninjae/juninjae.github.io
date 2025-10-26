---
title: "KSAE Student Competition"
date: 2020-08-08
image: /assets/images/life/RTY/thumbnail.jpg
images:
  - /assets/images/life/RTY/thumbnail.jpg
  - /assets/images/life/RTY/image1.png
  - /assets/images/life/RTY/video1.mp4
  - /assets/images/life/RTY/image2.jpg
  - /assets/images/life/RTY/image3.jpg
---

<!-- Image/Video Carousel -->
{% if page.images %}
<div class="mb-4">
  {% capture carousel_images %}{% for image in page.images %}{{ image }}
{% endfor %}{% endcapture %}
  {% assign post_id = page.path | split: "/" | last | split: "." | first %}
  {% include elements/carousel.html carousel_id="life-{{ post_id }}" carousel_images=carousel_images %}
</div>
{% endif %}

<!-- Date -->
<div class="mb-3">
  <p class="text-muted">
    <i class="fas fa-calendar-alt"></i> {{ page.date | date: "%B %d, %Y" }}
  </p>
</div>

Participated in the National Student Automobile Competition (KSAE) with our dedicated team. After months of intensive preparation and hard work from all team members, we successfully completed our vehicle design and testing.

The competition was an incredible learning experience that challenged us to apply our engineering knowledge in real-world scenarios. Our team's collaboration and determination throughout the entire process made this project truly memorable. 🏁

---
layout: page
title: CV
permalink: /cv/
weight: 4
---

{% assign cv_path = "/assets/publications/Injae_Jun_CV.pdf" %}

<div class="d-grid gap-2 d-md-flex justify-content-md-start mb-3">
  <a class="btn btn-outline-primary" href="{{ cv_path | relative_url }}">Open CV (PDF)</a>
  <a class="btn btn-outline-secondary" href="{{ cv_path | relative_url }}" download>Download</a>
</div>

<iframe src="{{ cv_path | relative_url }}" style="width:100%; height:80vh; border:none;"></iframe>



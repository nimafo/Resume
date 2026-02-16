---
layout: page
title: project 1
description: with background image
img: assets/img/12.jpg
importance: 1
category: work
related_publications: true
---

Every project has a beautiful feature showcase page.
It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.

To give your project a background in the portfolio page, just add the img tag to the front matter like so:

    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---

<hr>
<h2>PDF</h2>

<div class="row">
  <div class="col-12">
    <div style="width:100%; height:900px;">
      <iframe
        src="{{ '/assets/HPBD.pdf' | relative_url }}"
        width="100%"
        height="100%"
        style="border:0;"
      ></iframe>
    </div>

    <p style="margin-top:0.75rem;">
      <a href="{{ '/assets/HPBD.pdf' | relative_url }}" target="_blank" rel="noopener">
        Open PDF in new tab
      </a>
    </p>
  </div>
</div>
<hr>


```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}

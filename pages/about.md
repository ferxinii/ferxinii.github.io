---
layout: page
title: About
permalink: /about/
weight: 3
---


<img src="/assets/images/face.png" alt="Profile photo" width="170" style="float: right; margin-left: 15px; border-radius: 8px;" />

# **About Me**
I am **{{ site.author.name }}** :wave:,  
I believe I am in equal parts an Engineer, a Physicist and a Mathematician.
I like to model all kinds of things in sciences ranging from Physics, Biology, and Economics, especially using computational tools.
I enjoy music and hiking.

You may download my CV <a href="/pages/about/CV_07_sept_25.pdf" target="_blank">here</a>.

<div class="row" markdown="0">
<div class="col-lg" style="border-right: 2px solid #ccc; padding-right: 30px;">
    {% include about/skills.html title="Programming Skills" source=site.data.programming-skills %}
  </div>
  <div class="col-lg" style="padding-left: 30px;">
    {% include about/skills.html title="Other Skills" source=site.data.other-skills %}
  </div>
</div>

<div class="row" markdown="0">
{% include about/timeline.html %}
</div>

---
title: ""
read_time: false
layout: single
header:
  image: /assets/images/SaiGon_byNight.jpg
---

# About Me  

Hi! I'm Ricky from Saigon, Vietnam — a data enthusiast, an inquisitive mind, and an advocate for decisions backed by evidence.  

I am a **Distinction** Master of Business Analytics graduate from *The University of Western Australia*, where I received solid training in leveraging analytical tools and techniques to solve complex business problems. Armed with tools like **Power BI**, **Python**, and a strong coffee, I can bridge the gap between raw data and real-world decisions.  

Data might be my thing, but I promise I can talk about more than just KPIs.  

<img src="/assets/images/graduation.jpeg" style="width:100%; height:auto;" alt="Graduation Photo">


---

## 🎓 UWA Projects
<div class="grid__wrapper">
  {% assign uwa_projects = site.portfolio | where: "category", "uwa" %}
  {% for project in uwa_projects %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>

---

## 🛠 Personal Projects
<div class="grid__wrapper">
  {% assign personal_projects = site.portfolio | where: "category", "personal" %}
  {% for project in personal_projects %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>

---

## 📊 Dashboards
<div class="grid__wrapper">
  {% assign dashboards = site.portfolio | where: "category", "dashboard" %}
  {% for project in dashboards %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>

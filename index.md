---
title: "Berichte - Aldin Mukic"
---

# Arbeitsberichte
{% for k in site.klassen %}
  {%- assign eigene = site.pages | where: "klasse", k | where_exp: "p", "p.listed != false" -%}
  {%- assign externe = site.data.extern | where: "klasse", k -%}
  {%- assign alle = eigene | concat: externe | sort: "datum" | reverse %}

## {{ k }}

{% for b in alle -%}
{%- if b.url contains "://" %}{% assign link = b.url %}{% else %}{% assign link = b.url | relative_url %}{% endif -%}
- {{ b.datum | date: "%Y-%m-%d" }} - [{{ b.title }}]({{ link }}){% if b.hinweis %} ({{ b.hinweis }}){% endif %}
{% endfor %}
{% endfor %}

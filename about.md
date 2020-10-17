---
layout: default
title: About me
---

<!-- Title begin -->
<div class="home">
  {%- if page.title -%}
  <h1 class="page-heading">
    {{ page.title }}
  </h1>
  {%- endif -%}
</div>
<!-- Title end -->

{%- if site.author.name -%}
<h3>{{ site.author.name | escape }}</h3>
{%- endif -%}

{%- if site.author.email -%}
<p>
Email: <a class="u-email" href="mailto:{{ site.author.email }}">{{ site.author.email }}</a>
</p>
{%- endif -%}

{%- if site.author.description -%}
  {{ site.author.description | escape }}
{%- endif -%}

<!--
vim:ts=2:sw=2:tw=76
-->

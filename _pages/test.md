---
title: "Technical Tests"
permalink: "/test"
---
# Theme Technical Testing
This page contains tests of technical aspects of the theme I am using and Jekyll in general.

{{ site.author.name }}

{{ site.author.name | escape }}

{%- assign default_paths = site.pages | map: "path" -%}
{%- assign page_paths = site.header_pages | default: default_paths -%}
{%- assign titles_size = site.pages | map: 'title' | join: '' | size -%}

{{ "/" | relative_url }}
{{ site.title | escape }}

{{ default_paths }}
{{ page_paths }}
{{ site.pages }}
{{ site.pages | map: 'title' | join: '' }}
{{ titles_size }}

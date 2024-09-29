---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
output:
  blogdown::html_page:
    toc: true
---


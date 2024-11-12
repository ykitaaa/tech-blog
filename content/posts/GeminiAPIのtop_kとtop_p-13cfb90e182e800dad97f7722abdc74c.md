---
title: "GeminiAPIのtop_kとtop_p"
date: "2024-11-12T11:13:00.000Z"
lastmod: "2024-11-12T12:46:00.000Z"
draft: true
hidden: true
series: []
nositemap: true
authors:
  - "YutaKita"
tags: []
categories: []
NOTION_METADATA:
  object: "page"
  id: "13cfb90e-182e-800d-ad97-f7722abdc74c"
  created_time: "2024-11-12T11:13:00.000Z"
  last_edited_time: "2024-11-12T12:46:00.000Z"
  created_by:
    object: "user"
    id: "11d54c62-5c86-4d27-a64b-4fdfb07609d7"
  last_edited_by:
    object: "user"
    id: "11d54c62-5c86-4d27-a64b-4fdfb07609d7"
  cover: null
  icon: null
  parent:
    type: "database_id"
    database_id: "ffffb90e-182e-8161-8a7c-c191eda82682"
  archived: false
  in_trash: false
  properties:
    hidden:
      id: "%40%3Bf%3D"
      type: "checkbox"
      checkbox: true
    series:
      id: "B%3C%3FS"
      type: "multi_select"
      multi_select: []
    draft:
      id: "JiWU"
      type: "checkbox"
      checkbox: true
    nositemap:
      id: "JuyN"
      type: "checkbox"
      checkbox: true
    authors:
      id: "bK%3B%5B"
      type: "people"
      people:
        - object: "user"
          id: "11d54c62-5c86-4d27-a64b-4fdfb07609d7"
          name: "YutaKita"
          avatar_url: null
          type: "person"
          person:
            email: "tomamekuchi@gmail.com"
    custom-front-matter:
      id: "c~kA"
      type: "rich_text"
      rich_text: []
    tags:
      id: "jw%7CC"
      type: "multi_select"
      multi_select: []
    categories:
      id: "nbY%3F"
      type: "multi_select"
      multi_select: []
    summary:
      id: "x%3AlD"
      type: "rich_text"
      rich_text: []
    Name:
      id: "title"
      type: "title"
      title:
        - type: "text"
          text:
            content: "GeminiAPIのtop_kとtop_p"
            link: null
          annotations:
            bold: false
            italic: false
            strikethrough: false
            underline: false
            code: false
            color: "default"
          plain_text: "GeminiAPIのtop_kとtop_p"
          href: null
  url: "https://www.notion.so/GeminiAPI-top_k-top_p-13cfb90e182e800dad97f7722abdc\
    74c"
  public_url: null
UPDATE_TIME: "2024-11-12T21:18:23.505Z"

---


# Googleのコメント


```xml

Top-K and top-P

Like temperature, top-K and top-P parameters are also used to control the diversity of the model's output.

Top-K is a positive integer that defines the number of most probable tokens from which to select the output token. A top-K of 1 selects a single token, performing greedy decoding.

Top-P defines the probability threshold that, once cumulatively exceeded, tokens stop being selected as candidates. A top-P of 0 is typically equivalent to greedy decoding, and a top-P of 1 typically selects every token in the model's vocabulary.

When both are supplied, the Gemini API will filter top-K tokens first, then top-P and then finally sample from the candidate tokens using the supplied temperature.

Run this example a number of times, change the settings and observe the change in output.
```


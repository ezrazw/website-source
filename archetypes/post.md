---
title: "{{ replace .TranslationBaseName "-" " " | title }}"
cover: "/covers/cover.jpg"
tags: ["tagA", "tagB"]
date: {{ .Date }}
draft: true
slug: "{{ replace .Name " " "-" | title | lower }}"
---

Cut out summary from your post content here.

<!--more-->

The remaining content of your post.

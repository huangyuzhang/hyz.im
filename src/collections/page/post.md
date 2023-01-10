---
title: 文章列表
path: post
date: 2022-01-10
layout: list-post
permalink: "/post/{% if pagination.pageNumber > 0 %}/page/{{ pagination.pageNumber + 1 }}{% endif %}/index.html"
pagination:
    data: collections.post
    size: 10
    alias: posts
    reverse: true
---

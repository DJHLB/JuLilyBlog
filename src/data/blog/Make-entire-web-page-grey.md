---
auther: DJLHB
pubDatetime: 2024-01-19T18:07:14+08:00
modDatetime: 2024-01-19T18:07:14+08:00
title: 使网页整体变灰
slug: Make-entire-web-page-grey
featured: false
draft: false
tags:
  - Web
description:
  使网页整体变灰
---

在HTML 的head标签里加入如下代码即可
```html
<style type="text/css">
html {
filter: progid:DXImageTransform.Microsoft.BasicImage(grayscale=1);
-webkit-filter: grayscale(100%);}
</style>
```

---
title: "Centroid"
category: Houdini/Wrangle
tags: 
created_at: 2016-04-13 11:02:58 +0900
updated_at: 2016-04-13 11:02:58 +0900
published: true
number: 34
---

```
vector min, max;
getbbox(0, min, max);
vector center = (min + max) / 2;
```

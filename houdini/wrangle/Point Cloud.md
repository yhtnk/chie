---
title: "Point Cloud"
category: Houdini/Wrangle
tags: 
created_at: 2016-04-21 16:20:55 +0900
updated_at: 2016-04-21 19:26:18 +0900
published: true
number: 47
---

```
float radius = chf("radius");
int maxpoints = chi("maxpoints");

int handle = pcopen(1, "P", @P, radius, maxpoints);
v@v = pcfilter(handle, "v");
pcclose(handle);
```

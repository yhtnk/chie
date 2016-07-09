---
title: "inputのセンターにpointを作る"
category: Houdini/Wrangle
tags: 
created_at: 2016-06-13 11:29:45 +0900
updated_at: 2016-06-13 11:29:46 +0900
published: true
number: 80
---

```
vector min, max;
getbbox(min, max);
vector center = (min + max) / 2;

removepoint(0, @ptnum);
addpoint(0, center);
```
`getbbox()`を使い、センターの座標を作り
`removepoint(0, @ptnum);`で、inputのpointをすべて消し
`addpoint(0, center);`で、センターにひとつだけpointを作成する

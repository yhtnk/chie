---
title: "leap -mixと同義"
category: Houdini/Wrangle
tags: 
created_at: 2016-04-21 19:29:10 +0900
updated_at: 2016-04-21 19:29:10 +0900
published: true
number: 48
---

```
float bias = chf("bias");
@Cd = lerp({1,0,0}, {0,1,0}, bias);
```
biasを0 ~ 1でアニメーションすることによって
第一引数から第二引数へ値が移っていく

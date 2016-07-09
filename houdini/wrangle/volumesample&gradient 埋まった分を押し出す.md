---
title: "volumesample&gradient 埋まった分を押し出す"
category: Houdini/Wrangle
tags: 
created_at: 2016-04-06 19:39:05 +0900
updated_at: 2016-04-27 19:17:24 +0900
published: true
number: 26
---

```
float volsample = volumesample(1, 0, @P);
vector volgrad = volumegradient(1, 0, @P);

vector pushout = volgrad * -volsample;
@P = @P + pushout;
```

`vector pushOut = volumegrad * -volsample;`は、埋まっているところを表面まで押し出す式
`vector pushOut = volumegrad * -volsample * 2;`にすると、埋まってる量外側に膨らむ

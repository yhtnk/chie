---
title: "Quaternion"
category: Houdini/Wrangle
tags: 
created_at: 2016-04-13 11:54:53 +0900
updated_at: 2016-04-13 11:54:53 +0900
published: true
number: 35
---

```
float deg = rand(@id) * 360;
float rad = radians(deg);

p@rot = quaternion(rad, normalize(@N));
```

`vector4 quaternion(float angle, vector axis)`

`float deg = rand(@id) * 360;`でランダムなAngleを作っている
継続的な回転をさせる場合などは、ここに式を書き足す
quaternionはradian(弧度)で角度を受け取るので、`float rad = radians(deg);`で変換する
axisを与える時は`normalize`してから与えないとうまく評価されない

以下はヘルプに書いてある別の書き方
`vector4 quaternion(matrix3 rotations)`
`vector4 quaternion(vector angleaxis)`

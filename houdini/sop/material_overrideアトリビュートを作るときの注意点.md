# コードサンプル
```
geo = hou.pwd().geometry()
mo_attr = geo.addAttrib(hou.attribType.Point, "material_override", '')

points = geo.points()

dict = {'file':''}

for point in points:
    path = '$HIP/ifdarc/ifdarchive_models/ifdarchive_models.%04d.bgeo.sc' % int(float(point.number()) % 4 + 1)
    dict['file'] = path
    point.setAttribValue("material_override", str(dict))
```

# 解説
`mo_attr = geo.addAttrib(hou.attribType.Point, "material_override", '')`
pointAttributeをaddする。いきなりsetはできないので、入れ物を用意する

`points = geo.points()`
pointを格納

`dict = {'file':''}`
dict型の変数を定義
この場合は、`file`パラメータをオーバーライドしたかったので、キーは`file`

`path = '$HIP/ifdarc/ifdarchive_models/ifdarchive_models.%04d.bgeo.sc' % int(float(point.number()) % 4 + 1)`
キーに対する値のほうのパスを作る
`point.number() % 4`では、エラーが出る。intは扱えないということなので、
`float(point.number() % 4)`とする、そうするとfloatで値が返ってくるので、
そのままでもおそらく大丈夫だが一応`int(float(point.number() % 4))`でint型にもどしてやる

`dict['file'] = path`
キー`file`に値を入れる

`point.setAttribValue("material_override", str(dict))`
今回一番トラップめいたところ
アトリビュートをセットするのだが`material_override`はstring型のアトリビュート
大して、dict型で変数を作っているので、
`point.setAttribValue("material_override", dict)`
こうしてしまうとエラーが出る
`dict`がstringになっていないから、`str(dict)`で文字列に直してやらなければならない

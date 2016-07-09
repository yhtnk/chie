```
int pl = addprim(0, "polyline");

for(int i = 0; i < @numpt; i++){
    addvertex(0, pl, i);
}
```

この場合はすでにpointが存在するという前提

まずは、polylineを作る
`int pl = addprim(0, "polyline");`

vertexは必ず無ければならないので、次にvertexを作る
そしてpointナンバーが第3引数になるので
`for(int i = 0; i < @numpt; i++)`として@numpt（pointの総数）分まわし、vertexを作る


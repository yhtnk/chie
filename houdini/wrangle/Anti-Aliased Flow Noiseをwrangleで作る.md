# コード
```
#include <voplib.h>

float amplitude = chf("amp");
vector frequency = chv("freq");
vector offset = chv("offset");
float roughness = chf("rough");
int maxoctaves = chi("maxoct");
float flow = chf("flow");
float flowrate = chf("fr");
float advection = chf("adv");


//float : FV, FP//
//vector : VV, VP//
float noise = vop_fbmFlowNoiseFV(@P * frequency - offset, roughness, maxoctaves, flow, flowrate, advection) * amplitude;

v@P = set(@P.x, @P.y + noise, @P.z);
```

# 解説
`#include <voplib.h>`
`$HH/vex/include`の`voplib.h`を読み込んでくる
これにより、`vop_fbmFlowNoiseFV`等が使えるようになる

```
float amplitude = chf("amp");
vector frequency = chv("freq");
vector offset = chv("offset");
float roughness = chf("rough");
int maxoctaves = chi("maxoct");
float flow = @Time;
float flowrate = chf("fr");
float advection = chf("adv");
```
各アトリビュートを変数に入れる
ラベルは直接書き込むことが出来ないので、後ほど`Parameter Interface`から調整する

`vop_fbmFlowNoiseFV(@P * frequency - offset, roughness, maxoctaves, flow, flowrate, advection) * amplitude;`
これが、AA Flow Noiseのコード

`v@P = set(@P.x, @P.y + noise, @P.z);`
ただ、Y軸に突っ込んでるだけなので、ここは自由に調整

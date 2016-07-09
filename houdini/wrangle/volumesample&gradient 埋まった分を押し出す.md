```
float volsample = volumesample(1, 0, @P);
vector volgrad = volumegradient(1, 0, @P);

vector pushout = volgrad * -volsample;
@P = @P + pushout;
```

`vector pushOut = volumegrad * -volsample;`は、埋まっているところを表面まで押し出す式
`vector pushOut = volumegrad * -volsample * 2;`にすると、埋まってる量外側に膨らむ

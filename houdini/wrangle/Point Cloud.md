```
float radius = chf("radius");
int maxpoints = chi("maxpoints");

int handle = pcopen(1, "P", @P, radius, maxpoints);
v@v = pcfilter(handle, "v");
pcclose(handle);
```

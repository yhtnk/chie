# コード

## pcfarthest(範囲内で最も遠いpointへの距離を返す）を使う場合 <おすすめ>
```
float radius = chf("radius");
int maxp = chi("maxpoints");

f@farthest;
i@farthest_point;

int handle = pcopen(0, "P", @P, radius, maxp);
@farthest = pcfarthest(handle);
pcclose(handle);

for(int i = 0; i < @numpt; i++){
    if(@farthest == distance(@P, point(0, "P", i))){
        @farthest_point = i;
    }
}
```
## pointcloudを使わない
```
float dist = 0;
float maxdist = 0;
int farthest;
i@farthest_point;
f@farthest;

for(int i = 0; i < @numpt; i++){
    vector p2 = point(0, "P", i);
    dist = distance(@P, p2);

    if(maxdist < dist){
        farthest = i;
        maxdist = dist;
    }
}

@farthest_point = farthest;
@farthest = maxdist;
```
# 説明
## pcfarthest(範囲内で最も遠いpointへの距離を返す）を使う場合 <おすすめ>
```
int handle = pcopen(0, "P", @P, radius, maxp);
@farthest = pcfarthest(handle);
pcclose(handle);
```
pcfarthestが範囲内（radiusで指定した範囲にある最大point数内）の最も遠いpointへの距離を出してくれる
inputされているpointの中で最も遠いpointでは無い点に注意が必要
```
for(int i = 0; i < @numpt; i++){
    if(@farthest == distance(@P, point(0, "P", i))){
        @farthest_point = i;
    }
}
```
pcfarthestで最大距離は出るが、その距離にあるpointnumberはでないので、
for文でpointnumberをまわし、distanceを測り、@farthestと同じ数字になるpointナンバーを@farthest_pointに突っ込む

## pointcloudを使わない
wrangleはもともと@ptnum毎にVEXpressionをまわすfor文のようなノードなので、
自分自身とどこかのpointを比較する場合for文はひとつで良い
こちらの書き方は、inputされているpointすべてに影響がある点がpcfarthestを使う場合との違い
```
vector p2 = point(0, "P", i);
dist = distance(@P, p2);
```
各pointとの距離をdistに入れてif文に送る
```
    if(maxdist < dist){
        farthest = i;
        maxdist = dist;
    }
```
2点間を比較してdistが大きかった場合は、そのpoint番号をとっておき、maxdistにdistをいれる
最終的に、`farthest`に入っていたpointが自分自身から離れているpoint番号になる
同時に最終的なmaxdistが最大距離になる
```
@farthest_point = farthest;
@farthest = maxdist;
```
この二つをアトリビュートに入れて完了

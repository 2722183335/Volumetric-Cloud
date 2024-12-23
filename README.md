# Volumetric-Cloud
体积云

## AABB检测

![AABB检测](https://github.com/2722183335/Volumetric-Cloud/blob/main/src/img/aabb1.png?raw=true)

``` shader
 float2 intersectAABB(float3 rayOrigin, float3 rayDir, float3 boxMin, float3 boxMax)
    {
        float3 tMin = (boxMin - rayOrigin) / rayDir;
        float3 tMax = (boxMax - rayOrigin) / rayDir;
        //反方向的
        float3 t1 = min(tMin, tMax);
        //正方向的
        float3 t2 = max(tMin, tMax);
        //计算最大的
        float tNear = max(max(t1.x, t1.y), t1.z);
        float tFar = min(min(t2.x, t2.y), t2.z);
        return float2(tNear, tFar);
    }
```

> [UNREAL MATERIAL COOKBOOK](../README.md) / [Advanced](README.md) / Texture LOD Caculate.md
## Texture LOD Caculate
version #1

Texture LOD Caculate
    
    float2 dx = ddx(uv * 512); 
    float2 dy = ddy(uv * 512); 
    float d = max(dot(dx, dx), dot(dy, dy)); 
    tex2Dlod(tex, float4(uv, 0, log2(sqrt(d))));


version #2

    float mip_map_level(in float2 texture_coordinate) // in texel units
    {
      float2  dx_vtc  = ddx(texture_coordinate);
      float2  dy_vtc  = ddy(texture_coordinate);
      float delta_max_sqr = max(dot(dx_vtc, dx_vtc), dot(dy_vtc, dy_vtc));
      return 0.5 * log2(delta_max_sqr);
    }
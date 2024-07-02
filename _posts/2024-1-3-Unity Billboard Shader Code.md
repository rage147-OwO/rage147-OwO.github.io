title: "Unity Billboard Shader Code"
categories:
 - VRCHAT
---
#Unity Billboard Shader Code : 네이버 블로그








카메라를 바라보는 Shader





 




```
Shader "Billboard"
{
 Properties
 {
 \_MainTex("Texture", 2D) = "white" {}
 \_Color("Color", Color) = (1,1,1,1)
 \_Number("Number", Range(0, 9)) = 0
 }
 SubShader
 {
 Tags { "IGNOREPROJECTOR" = "true" "RenderType" = "Transparent" "Queue" = "Transparent+500" } //"LIGHTMODE"="FORWARDBASE" "QUEUE"="AlphaTest" "IGNOREPROJECTOR"="true" "SHADOWSUPPORT"="true" "RenderType"="TransparentCutout" "DisableBatching"="LodFading"
 LOD 100

 Pass
 {

 //ZTest Off
 Blend SrcAlpha OneMinusSrcAlpha
 Cull Off

 CGPROGRAM

 #pragma vertex vert
 #pragma fragment frag
 #pragma multi\_compile\_instancing
 // make fog work
 #pragma multi\_compile\_fog

 #include "UnityCG.cginc"

 struct appdata
 {
 float4 vertex : POSITION;
 float2 uv : TEXCOORD0;
 float4 color : COLOR;
 UNITY\_VERTEX\_INPUT\_INSTANCE\_ID
 };

 struct v2f
 {
 float2 uv : TEXCOORD0;
 UNITY\_FOG\_COORDS(1)
 float4 vertex : SV\_POSITION;
 float4 color : COLOR0;
 UNITY\_VERTEX\_INPUT\_INSTANCE\_ID // necessary only if you want to access instanced properties in fragment Shader.
 };

 sampler2D \_MainTex;
 float4 \_MainTex\_ST;

 UNITY\_INSTANCING\_BUFFER\_START(Props)
 UNITY\_DEFINE\_INSTANCED\_PROP(float4, \_Color)
 UNITY\_INSTANCING\_BUFFER\_END(Props)


 v2f vert(appdata v)
 {
 v2f o;

 UNITY\_SETUP\_INSTANCE\_ID(v);
 UNITY\_TRANSFER\_INSTANCE\_ID(v, o); // necessary only if you want to access instanced properties in the fragment Shader.


 //copy them so we can change them (demonstration purpos only)
 float4x4 newViewMatrix = UNITY\_MATRIX\_V;

 //break out the axis
 float3 right = normalize(newViewMatrix.\_m00\_m01\_m02);
 float3 up = normalize(newViewMatrix.\_m10\_m11\_m12);
 float3 forward = normalize(newViewMatrix.\_m20\_m21\_m22);

 
 //get the rotation parts of the matrix
 float4x4 rotationMatrix = float4x4(
 right, 0,
 up, 0,
 forward, 0,
 0, 0, 0, 1);

 //the inverse of a rotation matrix happens to always be the transpose
 float4x4 rotationMatrixInverse = transpose(rotationMatrix);

 //apply the rotationMatrixInverse, model, view and projection matrix
 float4 pos = v.vertex;
 pos = mul(rotationMatrixInverse, pos);
 pos = mul(UNITY\_MATRIX\_M, pos);
 pos = mul(newViewMatrix, pos);
 pos = mul(UNITY\_MATRIX\_P, pos);
 o.vertex = pos;

 o.uv = TRANSFORM\_TEX(v.uv, \_MainTex);
 UNITY\_TRANSFER\_FOG(o,o.vertex);
 return o;
 }

 fixed4 frag(v2f i) : SV\_Target
 {
 // sample the texture
 fixed4 col = UNITY\_ACCESS\_INSTANCED\_PROP(Props, \_Color) \* tex2D(\_MainTex, i.uv);
 // apply fog
 UNITY\_APPLY\_FOG(i.fogCoord, col);
 UNITY\_SETUP\_INSTANCE\_ID(i); // necessary only if any instanced properties are going to be accessed in the fragment Shader.
 return col;
 }
 ENDCG
 }
 }
}
```





 



​
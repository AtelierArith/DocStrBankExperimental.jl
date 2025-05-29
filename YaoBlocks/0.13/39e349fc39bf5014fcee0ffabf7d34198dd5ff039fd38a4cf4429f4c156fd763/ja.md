```
RotationGate{D,T,GT<:AbstractBlock{D}} <: PrimitiveBlock{D}
```

RotationGateは、GTがエルミートかつ自己反射的です。

# 定義

式 `rot(G, θ)` は次のゲートを定義します

$$
\cos \frac{\theta}{2}I - i \sin \frac{\theta}{2} G
$$

```
RotationGate{D,T,GT<:AbstractBlock{D}} <: PrimitiveBlock{D}
```

RotationGate, with GT both hermitian and isreflexive.

# Definition

Expression `rot(G, θ)` defines the following gate

$$
\cos \frac{\theta}{2}I - i \sin \frac{\theta}{2} G
$$

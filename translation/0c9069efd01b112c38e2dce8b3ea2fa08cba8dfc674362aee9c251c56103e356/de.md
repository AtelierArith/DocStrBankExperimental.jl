```
normalize!(a::AbstractArray, p::Real=2)
```

Normalisieren Sie das Array `a` in-place, sodass seine `p`-Norm gleich eins ist, d.h. `norm(a, p) == 1`. Siehe auch [`normalize`](@ref) und [`norm`](@ref).

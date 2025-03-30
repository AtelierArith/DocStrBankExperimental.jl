```
(I::UniformScaling)(n::Integer)
```

Bir `UniformScaling`'den bir `Diagonal` matris oluşturur.

!!! compat "Julia 1.2"
    Bu yöntem Julia 1.2 itibarıyla mevcuttur.


# Örnekler

```jldoctest
julia> I(3)
3×3 Diagonal{Bool, Vector{Bool}}:
 1  ⋅  ⋅
 ⋅  1  ⋅
 ⋅  ⋅  1

julia> (0.7*I)(3)
3×3 Diagonal{Float64, Vector{Float64}}:
 0.7   ⋅    ⋅
  ⋅   0.7   ⋅
  ⋅    ⋅   0.7
```

```
vect(X...)
```

Bir [`Vector`](@ref) oluşturur, eleman türü argümanın `promote_typeof`'undan hesaplanır ve argüman listesini içerir.

# Örnekler

```jldoctest
julia> a = Base.vect(UInt8(1), 2.5, 1//2)
3-element Vector{Float64}:
 1.0
 2.5
 0.5
```

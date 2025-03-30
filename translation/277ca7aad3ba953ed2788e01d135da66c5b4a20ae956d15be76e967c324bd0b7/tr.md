```
float(x)
```

Bir sayıyı veya diziyi kayan nokta veri türüne dönüştürür.

Ayrıca bakınız: [`complex`](@ref), [`oftype`](@ref), [`convert`](@ref).

# Örnekler

```jldoctest
julia> float(1:1000)
1.0:1.0:1000.0

julia> float(typemax(Int32))
2.147483647e9
```

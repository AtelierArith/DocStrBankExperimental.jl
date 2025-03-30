```
clamp(x, T)::T
```

`x` değerini `typemin(T)` ve `typemax(T)` arasında sınırlayın ve sonucu `T` türüne dönüştürün.

Ayrıca bkz. [`trunc`](@ref).

# Örnekler

```jldoctest
julia> clamp(200, Int8)
127

julia> clamp(-200, Int8)
-128

julia> trunc(Int, 4pi^2)
39
```

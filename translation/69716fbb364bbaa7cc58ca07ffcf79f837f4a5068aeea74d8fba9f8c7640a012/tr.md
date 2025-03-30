```
abs2(x)
```

`x`'in kare mutlak değeri.

Bu, özellikle `abs(x)`'in bir karekök gerektirdiği karmaşık sayılar için `abs(x)^2`'den daha hızlı olabilir, [`hypot`](@ref) aracılığıyla.

Ayrıca bkz. [`abs`](@ref), [`conj`](@ref), [`real`](@ref).

# Örnekler

```jldoctest
julia> abs2(-3)
9

julia> abs2(3.0 + 4.0im)
25.0

julia> sum(abs2, [1+2im, 3+4im])  # LinearAlgebra.norm(x)^2
30
```

```
x && y
```

Kısa devre boolean VE.

Ayrıca bkz. [`&`](@ref), üçlü operatör `? :`, ve [kontrol akışı](@ref man-conditional-evaluation) ile ilgili kılavuz bölümü.

# Örnekler

```jldoctest
julia> x = 3;

julia> x > 1 && x < 10 && x isa Int
true

julia> x < 0 && error("beklenen pozitif x")
false
```

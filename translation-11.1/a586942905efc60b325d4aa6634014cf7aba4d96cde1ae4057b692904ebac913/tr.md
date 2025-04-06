```
div(x, y)
÷(x, y)
```

Euclidean (tam sayı) bölme işleminin sonucu. Genel olarak, kesirli bir parça olmadan matematiksel bir işlem olan x/y ile eşdeğerdir.

Ayrıca bakınız: [`cld`](@ref), [`fld`](@ref), [`rem`](@ref), [`divrem`](@ref).

# Örnekler

```jldoctest
julia> 9 ÷ 4
2

julia> -5 ÷ 3
-1

julia> 5.0 ÷ 2
2.0

julia> div.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -1  -1  -1  0  0  0  0  0  1  1  1
```

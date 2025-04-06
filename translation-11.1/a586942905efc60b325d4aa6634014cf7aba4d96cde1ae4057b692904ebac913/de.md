```
div(x, y)
÷(x, y)
```

Der Quotient aus der euklidischen (ganzzahligen) Division. Allgemein äquivalent zu einer mathematischen Operation x/y ohne einen Bruchteil.

Siehe auch: [`cld`](@ref), [`fld`](@ref), [`rem`](@ref), [`divrem`](@ref).

# Beispiele

```jldoctest
julia> 9 ÷ 4
2

julia> -5 ÷ 3
-1

julia> 5.0 ÷ 2
2.0

julia> div.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) mit eltype Int64:
 -1  -1  -1  0  0  0  0  0  1  1  1
```

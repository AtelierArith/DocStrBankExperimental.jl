```
cld(x, y)
```

Plus petit entier supérieur ou égal à `x / y`. Équivalent à `div(x, y, RoundUp)`.

Voir aussi [`div`](@ref), [`fld`](@ref).

# Exemples

```jldoctest
julia> cld(5.5, 2.2)
3.0

julia> cld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) avec eltype Int64:
 -1  -1  -1  0  0  0  1  1  1  2  2
```

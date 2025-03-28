```
div(x, y)
÷(x, y)
```

Le quotient de la division euclidienne (entière). Généralement équivalent à une opération mathématique x/y sans partie fractionnaire.

Voir aussi : [`cld`](@ref), [`fld`](@ref), [`rem`](@ref), [`divrem`](@ref).

# Exemples

```jldoctest
julia> 9 ÷ 4
2

julia> -5 ÷ 3
-1

julia> 5.0 ÷ 2
2.0

julia> div.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) avec eltype Int64:
 -1  -1  -1  0  0  0  0  0  1  1  1
```

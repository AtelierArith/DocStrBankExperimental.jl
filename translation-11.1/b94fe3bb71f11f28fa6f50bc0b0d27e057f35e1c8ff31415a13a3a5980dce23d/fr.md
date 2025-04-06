```
rem(x, y)
%(x, y)
```

Reste de la division euclidienne, retournant une valeur du même signe que `x`, et de magnitude inférieure à `y`. Cette valeur est toujours exacte.

Voir aussi : [`div`](@ref), [`mod`](@ref), [`mod1`](@ref), [`divrem`](@ref).

# Exemples

```jldoctest
julia> x = 15; y = 4;

julia> x % y
3

julia> x == div(x, y) * y + rem(x, y)
true

julia> rem.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) avec eltype Int64:
 -2  -1  0  -2  -1  0  1  2  0  1  2
```

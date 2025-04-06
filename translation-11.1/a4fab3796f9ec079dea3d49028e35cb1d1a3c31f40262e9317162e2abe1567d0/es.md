```
typeof(x)
```

Obtén el tipo concreto de `x`.

Consulta también [`eltype`](@ref).

# Ejemplos

```jldoctest
julia> a = 1//2;

julia> typeof(a)
Rational{Int64}

julia> M = [1 2; 3.5 4];

julia> typeof(M)
Matrix{Float64} (alias for Array{Float64, 2})
```

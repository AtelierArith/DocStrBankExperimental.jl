```
broadcast!(f, dest, As...)
```

Comme [`broadcast`](@ref), mais stocke le résultat de `broadcast(f, As...)` dans le tableau `dest`. Notez que `dest` est uniquement utilisé pour stocker le résultat et ne fournit pas d'arguments à `f` à moins qu'il ne soit également listé dans les `As`, comme dans `broadcast!(f, A, A, B)` pour effectuer `A[:] = broadcast(f, A, B)`.

# Exemples

```jldoctest
julia> A = [1.0; 0.0]; B = [0.0; 0.0];

julia> broadcast!(+, B, A, (0, -2.0));

julia> B
2-element Vector{Float64}:
  1.0
 -2.0

julia> A
2-element Vector{Float64}:
 1.0
 0.0

julia> broadcast!(+, A, A, (0, -2.0));

julia> A
2-element Vector{Float64}:
  1.0
 -2.0
```

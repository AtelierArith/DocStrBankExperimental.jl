```
vect(X...)
```

Crée un [`Vector`](@ref) avec un type d'élément calculé à partir du `promote_typeof` de l'argument, contenant la liste des arguments.

# Exemples

```jldoctest
julia> a = Base.vect(UInt8(1), 2.5, 1//2)
3-element Vector{Float64}:
 1.0
 2.5
 0.5
```

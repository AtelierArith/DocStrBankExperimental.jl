```
Iterators.map(f, iterators...)
```

Créez un mappage paresseux. C'est une autre syntaxe pour écrire `(f(args...) for args in zip(iterators...))`.

!!! compat "Julia 1.6"
    Cette fonction nécessite au moins Julia 1.6.


# Exemples

```jldoctest
julia> collect(Iterators.map(x -> x^2, 1:3))
3-element Vector{Int64}:
 1
 4
 9
```

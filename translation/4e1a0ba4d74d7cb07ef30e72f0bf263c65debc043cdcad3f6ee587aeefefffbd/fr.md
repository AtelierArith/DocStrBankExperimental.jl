```
ntuple(f, n::Integer)
```

Crée un tuple de longueur `n`, en calculant chaque élément comme `f(i)`, où `i` est l'index de l'élément.

# Exemples

```jldoctest
julia> ntuple(i -> 2*i, 4)
(2, 4, 6, 8)
```

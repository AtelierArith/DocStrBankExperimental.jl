```
partialsortperm(v, k; by=identity, lt=isless, rev=false)
```

Renvoie une permutation partielle `I` du vecteur `v`, de sorte que `v[I]` renvoie les valeurs d'une version entièrement triée de `v` à l'index `k`. Si `k` est une plage, un vecteur d'indices est renvoyé ; si `k` est un entier, un seul indice est renvoyé. L'ordre est spécifié en utilisant les mêmes mots-clés que `sort!`. La permutation est stable : les indices des éléments égaux apparaîtront dans l'ordre croissant.

Cette fonction est équivalente à, mais plus efficace que, l'appel à `sortperm(...)[k]`.

# Exemples

```jldoctest
julia> v = [3, 1, 2, 1];

julia> v[partialsortperm(v, 1)]
1

julia> p = partialsortperm(v, 1:3)
3-element view(::Vector{Int64}, 1:3) with eltype Int64:
 2
 4
 3

julia> v[p]
3-element Vector{Int64}:
 1
 1
 2
```

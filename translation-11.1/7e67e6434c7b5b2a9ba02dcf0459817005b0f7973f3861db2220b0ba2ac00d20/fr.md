```
Pair(x, y)
x => y
```

Construisez un objet `Pair` de type `Pair{typeof(x), typeof(y)}`. Les éléments sont stockés dans les champs `first` et `second`. Ils peuvent également être accessibles via l'itération (mais un `Pair` est traité comme un "scalaire" unique pour les opérations de diffusion).

Voir aussi [`Dict`](@ref).

# Exemples

```jldoctest
julia> p = "foo" => 7
"foo" => 7

julia> typeof(p)
Pair{String, Int64}

julia> p.first
"foo"

julia> for x in p
           println(x)
       end
foo
7

julia> replace.(["xops", "oxps"], "x" => "o")
2-element Vector{String}:
 "oops"
 "oops"
```

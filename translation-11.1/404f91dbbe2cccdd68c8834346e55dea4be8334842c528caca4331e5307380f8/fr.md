```
applicable(f, args...) -> Bool
```

Déterminez si la fonction générique donnée a une méthode applicable aux arguments donnés.

Voir aussi [`hasmethod`](@ref).

# Exemples

```jldoctest
julia> function f(x, y)
           x + y
       end;

julia> applicable(f, 1)
false

julia> applicable(f, 1, 2)
true
```

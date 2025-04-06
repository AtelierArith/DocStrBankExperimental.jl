```
only(x)
```

Renvoie le seul et unique élément de la collection `x`, ou lève une [`ArgumentError`](@ref) si la collection contient zéro ou plusieurs éléments.

Voir aussi [`first`](@ref), [`last`](@ref).

!!! compat "Julia 1.4"
    Cette méthode nécessite au moins Julia 1.4.


# Exemples

```jldoctest
julia> only(["a"])
"a"

julia> only("a")
'a': ASCII/Unicode U+0061 (catégorie Ll: Lettre, minuscule)

julia> only(())
ERREUR : ArgumentError: Le tuple contient 0 éléments, doit contenir exactement 1 élément
Traceback :
[...]

julia> only(('a', 'b'))
ERREUR : ArgumentError: Le tuple contient 2 éléments, doit contenir exactement 1 élément
Traceback :
[...]
```

```
mktempdir(f::Function, parent=tempdir(); prefix="jl_")
```

Appliquez la fonction `f` au résultat de [`mktempdir(parent; prefix)`](@ref) et supprimez le répertoire temporaire ainsi que tout son contenu une fois terminé.

Voir aussi : [`mktemp`](@ref), [`mkdir`](@ref).

!!! compat "Julia 1.2"
    L'argument clé `prefix` a été ajouté dans Julia 1.2.


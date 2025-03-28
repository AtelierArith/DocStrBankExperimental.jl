```
mktemp(f::Function, parent=tempdir())
```

Appliquez la fonction `f` au résultat de [`mktemp(parent)`](@ref) et supprimez le fichier temporaire une fois terminé.

Voir aussi : [`mktempdir`](@ref).

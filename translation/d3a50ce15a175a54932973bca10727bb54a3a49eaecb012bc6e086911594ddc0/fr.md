```
ArgWrite = Union{AbstractString, AbstractCmd, IO}
```

Le type `ArgWrite` est une union des types que la fonction `arg_write` sait comment convertir en des poignées IO écrites, sauf pour `Nothing` que `arg_write` gère en générant un fichier temporaire. Voir [`arg_write`](@ref) pour plus de détails.

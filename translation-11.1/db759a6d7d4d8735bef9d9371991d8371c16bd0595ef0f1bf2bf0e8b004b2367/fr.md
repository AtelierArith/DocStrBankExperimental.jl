```
hardlink(src::AbstractString, dst::AbstractString)
```

Crée un lien dur vers un fichier source existant `src` avec le nom `dst`. La destination, `dst`, ne doit pas exister.

Voir aussi : [`symlink`](@ref).

!!! compat "Julia 1.8"
    Cette méthode a été ajoutée dans Julia 1.8.


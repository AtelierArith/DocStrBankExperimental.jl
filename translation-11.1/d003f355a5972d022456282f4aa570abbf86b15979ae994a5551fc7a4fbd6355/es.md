```
LibGit2.isdirty(repo::GitRepo, pathspecs::AbstractString=""; cached::Bool=false) -> Bool
```

Verifica si ha habido cambios en los archivos rastreados en el árbol de trabajo (si `cached=false`) o en el índice (si `cached=true`). `pathspecs` son las especificaciones para las opciones del diff.

# Ejemplos

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdirty(repo) # debería ser falso
open(joinpath(repo_path, new_file), "a") do f
    println(f, "aquí está mi nuevo archivo genial")
end
LibGit2.isdirty(repo) # ahora verdadero
LibGit2.isdirty(repo, new_file) # ahora verdadero
```

Equivalente a `git diff-index HEAD [-- <pathspecs>]`.

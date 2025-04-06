```
LibGit2.isdiff(repo::GitRepo, treeish::AbstractString, pathspecs::AbstractString=""; cached::Bool=false)
```

Verifica si hay diferencias entre el árbol especificado por `treeish` y los archivos rastreados en el árbol de trabajo (si `cached=false`) o el índice (si `cached=true`). `pathspecs` son las especificaciones para las opciones del diff.

# Ejemplos

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdiff(repo, "HEAD") # debería ser falso
open(joinpath(repo_path, new_file), "a") do f
    println(f, "aquí está mi genial nuevo archivo")
end
LibGit2.isdiff(repo, "HEAD") # ahora verdadero
```

Equivalente a `git diff-index <treeish> [-- <pathspecs>]`.

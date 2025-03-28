```
diff_files(repo::GitRepo, branch1::AbstractString, branch2::AbstractString; kwarg...) -> Vector{AbstractString}
```

Muestra qué archivos han cambiado en el repositorio git `repo` entre las ramas `branch1` y `branch2`.

El argumento de palabra clave es:

  * `filter::Set{Consts.DELTA_STATUS}=Set([Consts.DELTA_ADDED, Consts.DELTA_MODIFIED, Consts.DELTA_DELETED]))`, y establece opciones para el diff. El valor predeterminado es mostrar archivos añadidos, modificados o eliminados.

Devuelve solo los *nombres* de los archivos que han cambiado, *no* su contenido.

# Ejemplos

```julia
LibGit2.branch!(repo, "branch/a")
LibGit2.branch!(repo, "branch/b")
# añade un archivo al repositorio
open(joinpath(LibGit2.path(repo),"file"),"w") do f
    write(f, "hello repo
")
end
LibGit2.add!(repo, "file")
LibGit2.commit(repo, "add file")
# devuelve ["file"]
filt = Set([LibGit2.Consts.DELTA_ADDED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
# devuelve [] porque los archivos existentes no fueron modificados
filt = Set([LibGit2.Consts.DELTA_MODIFIED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
```

Equivalente a `git diff --name-only --diff-filter=<filter> <branch1> <branch2>`.

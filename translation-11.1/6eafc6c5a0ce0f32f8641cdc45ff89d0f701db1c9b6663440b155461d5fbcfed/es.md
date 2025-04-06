```
reset!(repo::GitRepo, id::GitHash, mode::Cint=Consts.RESET_MIXED)
```

Restablece el repositorio `repo` a su estado en `id`, utilizando uno de los tres modos establecidos por `mode`:

1. `Consts.RESET_SOFT` - mover HEAD a `id`.
2. `Consts.RESET_MIXED` - por defecto, mover HEAD a `id` y restablecer el índice a `id`.
3. `Consts.RESET_HARD` - mover HEAD a `id`, restablecer el índice a `id` y descartar todos los cambios en el trabajo.

# Ejemplos

```julia
# obtener cambios
LibGit2.fetch(repo)
isfile(joinpath(repo_path, our_file)) # será falso

# fusión rápida de los cambios
LibGit2.merge!(repo, fastforward=true)

# porque no había ningún archivo localmente, pero hay
# un archivo de forma remota, necesitamos restablecer la rama
head_oid = LibGit2.head_oid(repo)
new_head = LibGit2.reset!(repo, head_oid, LibGit2.Consts.RESET_HARD)
```

En este ejemplo, el remoto del que se está obteniendo *sí* tiene un archivo llamado `our_file` en su índice, por lo que debemos restablecer.

Equivalente a `git reset [--soft | --mixed | --hard] <id>`.

# Ejemplos

```julia
repo = LibGit2.GitRepo(repo_path)
head_oid = LibGit2.head_oid(repo)
open(joinpath(repo_path, "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
mode = LibGit2.Consts.RESET_HARD
# descartará los cambios en file1
# y lo desestará
new_head = LibGit2.reset!(repo, head_oid, mode)
```

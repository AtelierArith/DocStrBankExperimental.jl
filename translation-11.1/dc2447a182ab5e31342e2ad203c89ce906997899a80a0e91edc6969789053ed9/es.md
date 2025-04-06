```
branch!(repo::GitRepo, branch_name::AbstractString, commit::AbstractString=""; kwargs...)
```

Crea una nueva rama git en el repositorio `repo`. `commit` es el [`GitHash`](@ref), en forma de cadena, que será el inicio de la nueva rama. Si `commit` es una cadena vacía, se utilizará el HEAD actual.

Los argumentos clave son:

  * `track::AbstractString=""`: el nombre de la rama remota que esta nueva rama debería rastrear, si la hay. Si está vacío (el valor predeterminado), no se rastreará ninguna rama remota.
  * `force::Bool=false`: si es `true`, la creación de la rama se forzará.
  * `set_head::Bool=true`: si es `true`, después de que la creación de la rama finalice, la cabeza de la rama se establecerá como el HEAD de `repo`.

Equivalente a `git checkout [-b|-B] <branch_name> [<commit>] [--track <track>]`.

# Ejemplos

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.branch!(repo, "new_branch", set_head=false)
```

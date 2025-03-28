```
branch!(repo::GitRepo, branch_name::AbstractString, commit::AbstractString=""; kwargs...)
```

Wechseln Sie zu einem neuen Git-Zweig im `repo`-Repository. `commit` ist der [`GitHash`](@ref), in Form eines Strings, der den Start des neuen Zweigs darstellt. Wenn `commit` ein leerer String ist, wird der aktuelle HEAD verwendet.

Die Schlüsselwortargumente sind:

  * `track::AbstractString=""`: der Name des Remote-Zweigs, den dieser neue Zweig verfolgen soll, falls vorhanden. Wenn leer (der Standard), wird kein Remote-Zweig verfolgt.
  * `force::Bool=false`: wenn `true`, wird die Erstellung des Zweigs erzwungen.
  * `set_head::Bool=true`: wenn `true`, wird nach Abschluss der Erstellung des Zweigs der Zweigkopf als HEAD von `repo` gesetzt.

Entspricht `git checkout [-b|-B] <branch_name> [<commit>] [--track <track>]`.

# Beispiele

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.branch!(repo, "new_branch", set_head=false)
```

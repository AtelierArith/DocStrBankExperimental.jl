```
branch!(repo::GitRepo, branch_name::AbstractString, commit::AbstractString=""; kwargs...)
```

Créez une nouvelle branche git dans le dépôt `repo`. `commit` est le [`GitHash`](@ref), sous forme de chaîne, qui sera le début de la nouvelle branche. Si `commit` est une chaîne vide, le HEAD actuel sera utilisé.

Les arguments clés sont :

  * `track::AbstractString=""`: le nom de la branche distante que cette nouvelle branche doit suivre, le cas échéant. Si vide (par défaut), aucune branche distante ne sera suivie.
  * `force::Bool=false`: si `true`, la création de la branche sera forcée.
  * `set_head::Bool=true`: si `true`, après la création de la branche, le HEAD de la branche sera défini comme le HEAD de `repo`.

Équivalent à `git checkout [-b|-B] <branch_name> [<commit>] [--track <track>]`.

# Exemples

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.branch!(repo, "new_branch", set_head=false)
```

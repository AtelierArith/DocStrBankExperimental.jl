```
reset!(repo::GitRepo, id::GitHash, mode::Cint=Consts.RESET_MIXED)
```

Réinitialisez le dépôt `repo` à son état à `id`, en utilisant l'un des trois modes définis par `mode` :

1. `Consts.RESET_SOFT` - déplacez HEAD vers `id`.
2. `Consts.RESET_MIXED` - par défaut, déplacez HEAD vers `id` et réinitialisez l'index à `id`.
3. `Consts.RESET_HARD` - déplacez HEAD vers `id`, réinitialisez l'index à `id`, et abandonnez tous les changements en cours.

# Exemples

```julia
# récupérer les changements
LibGit2.fetch(repo)
isfile(joinpath(repo_path, our_file)) # sera faux

# fusion rapide des changements
LibGit2.merge!(repo, fastforward=true)

# parce qu'il n'y avait pas de fichier localement, mais qu'il y a
# un fichier à distance, nous devons réinitialiser la branche
head_oid = LibGit2.head_oid(repo)
new_head = LibGit2.reset!(repo, head_oid, LibGit2.Consts.RESET_HARD)
```

Dans cet exemple, le dépôt à partir duquel nous récupérons *a* un fichier appelé `our_file` dans son index, c'est pourquoi nous devons réinitialiser.

Équivalent à `git reset [--soft | --mixed | --hard] <id>`.

# Exemples

```julia
repo = LibGit2.GitRepo(repo_path)
head_oid = LibGit2.head_oid(repo)
open(joinpath(repo_path, "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
mode = LibGit2.Consts.RESET_HARD
# va abandonner les changements dans file1
# et le désindexer
new_head = LibGit2.reset!(repo, head_oid, mode)
```

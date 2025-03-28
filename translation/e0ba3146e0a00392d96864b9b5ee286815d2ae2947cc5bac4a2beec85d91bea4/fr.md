```
diff_files(repo::GitRepo, branch1::AbstractString, branch2::AbstractString; kwarg...) -> Vector{AbstractString}
```

Montre quels fichiers ont changé dans le dépôt git `repo` entre les branches `branch1` et `branch2`.

L'argument clé est :

  * `filter::Set{Consts.DELTA_STATUS}=Set([Consts.DELTA_ADDED, Consts.DELTA_MODIFIED, Consts.DELTA_DELETED]))`, et il définit les options pour le diff. La valeur par défaut est de montrer les fichiers ajoutés, modifiés ou supprimés.

Retourne uniquement les *noms* des fichiers qui ont changé, *pas* leur contenu.

# Exemples

```julia
LibGit2.branch!(repo, "branch/a")
LibGit2.branch!(repo, "branch/b")
# ajouter un fichier au dépôt
open(joinpath(LibGit2.path(repo),"file"),"w") do f
    write(f, "hello repo
")
end
LibGit2.add!(repo, "file")
LibGit2.commit(repo, "add file")
# retourne ["file"]
filt = Set([LibGit2.Consts.DELTA_ADDED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
# retourne [] car les fichiers existants n'ont pas été modifiés
filt = Set([LibGit2.Consts.DELTA_MODIFIED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
```

Équivalent à `git diff --name-only --diff-filter=<filter> <branch1> <branch2>`.

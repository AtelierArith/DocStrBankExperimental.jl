```
LibGit2.revcount(repo::GitRepo, commit1::AbstractString, commit2::AbstractString)
```

Liste le nombre de révisions entre `commit1` et `commit2` (OIDs de commit sous forme de chaîne). Étant donné que `commit1` et `commit2` peuvent être sur des branches différentes, `revcount` effectue une liste de révisions "gauche-droite" (et un compte), retournant un tuple d'`Int`s - le nombre de commits à gauche et à droite, respectivement. Un commit à gauche (ou à droite) fait référence à quel côté d'une différence symétrique dans un arbre le commit est accessible.

Équivalent à `git rev-list --left-right --count <commit1> <commit2>`.

# Exemples

```julia
repo = LibGit2.GitRepo(repo_path)
repo_file = open(joinpath(repo_path, test_file), "a")
println(repo_file, "hello world")
flush(repo_file)
LibGit2.add!(repo, test_file)
commit_oid1 = LibGit2.commit(repo, "commit 1")
println(repo_file, "hello world again")
flush(repo_file)
LibGit2.add!(repo, test_file)
commit_oid2 = LibGit2.commit(repo, "commit 2")
LibGit2.revcount(repo, string(commit_oid1), string(commit_oid2))
```

Cela retournera `(-1, 0)`.

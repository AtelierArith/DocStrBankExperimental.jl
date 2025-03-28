```
LibGit2.revcount(repo::GitRepo, commit1::AbstractString, commit2::AbstractString)
```

Listet die Anzahl der Revisionen zwischen `commit1` und `commit2` (committish OIDs in String-Form). Da `commit1` und `commit2` sich möglicherweise auf verschiedenen Branches befinden, führt `revcount` eine "links-rechts" Revisionliste (und Zählung) durch und gibt ein Tupel von `Int`s zurück - die Anzahl der linken und rechten Commits, jeweils. Ein linker (oder rechter) Commit bezieht sich darauf, von welcher Seite einer symmetrischen Differenz in einem Baum der Commit erreichbar ist.

Entspricht `git rev-list --left-right --count <commit1> <commit2>`.

# Beispiele

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

Dies wird `(-1, 0)` zurückgeben.

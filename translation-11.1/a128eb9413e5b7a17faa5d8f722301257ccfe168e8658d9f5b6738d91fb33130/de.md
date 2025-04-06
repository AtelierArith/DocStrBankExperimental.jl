```
add_push!(repo::GitRepo, rmt::GitRemote, push_spec::String)
```

Fügen Sie eine *push* refspec für das angegebene `rmt` hinzu. Diese refspec enthält Informationen darüber, welche(n) Branch(es) gepusht werden sollen.

# Beispiele

```julia-repl
julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, branch);

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```

!!! Hinweis     Möglicherweise müssen Sie [`close`](@ref) aufrufen und das betreffende `GitRemote` nach der Aktualisierung seiner Push-refspecs erneut öffnen, damit die Änderung wirksam wird und Aufrufe von [`push`](@ref) funktionieren.

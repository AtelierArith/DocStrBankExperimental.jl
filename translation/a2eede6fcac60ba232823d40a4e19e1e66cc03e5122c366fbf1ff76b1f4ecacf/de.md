```
add_fetch!(repo::GitRepo, rmt::GitRemote, fetch_spec::String)
```

Fügen Sie eine *fetch* refspec für das angegebene `rmt` hinzu. Diese refspec enthält Informationen darüber, von welchem(e) Branch(es) abgerufen werden soll.

# Beispiele

```julia-repl
julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```

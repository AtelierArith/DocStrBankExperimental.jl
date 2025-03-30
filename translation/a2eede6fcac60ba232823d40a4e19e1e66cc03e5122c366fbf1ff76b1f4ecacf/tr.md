```
add_fetch!(repo::GitRepo, rmt::GitRemote, fetch_spec::String)
```

Belirtilen `rmt` için bir *fetch* refspec ekleyin. Bu refspec, hangi dal(lar)ın alınacağına dair bilgileri içerecektir.

# Örnekler

```julia-repl
julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```

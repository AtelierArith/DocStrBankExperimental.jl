```
url(rmt::GitRemote)
```

Holen Sie sich die Fetch-URL eines Remote-Git-Repositorys.

# Beispiele

```julia-repl
julia> repo_url = "https://github.com/JuliaLang/Example.jl";

julia> repo = LibGit2.init(mktempdir());

julia> remote = LibGit2.GitRemote(repo, "origin", repo_url);

julia> LibGit2.url(remote)
"https://github.com/JuliaLang/Example.jl"
```

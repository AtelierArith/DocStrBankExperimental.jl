```
name(rmt::GitRemote)
```

Bir uzak depo adını alın, örneğin `"origin"`. Eğer uzak depo anonimse (bkz. [`GitRemoteAnon`](@ref)) ad boş bir dize `""` olacaktır.

# Örnekler

```julia-repl
julia> repo_url = "https://github.com/JuliaLang/Example.jl";

julia> repo = LibGit2.clone(cache_repo, "test_directory");

julia> remote = LibGit2.GitRemote(repo, "origin", repo_url);

julia> name(remote)
"origin"
```

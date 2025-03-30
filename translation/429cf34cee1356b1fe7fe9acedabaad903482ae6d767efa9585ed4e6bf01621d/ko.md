```
fetch_refspecs(rmt::GitRemote) -> Vector{String}
```

지정된 `rmt`에 대한 *fetch* refspecs를 가져옵니다. 이 refspecs는 어떤 브랜치를 가져올지에 대한 정보를 포함하고 있습니다.

# 예제

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```

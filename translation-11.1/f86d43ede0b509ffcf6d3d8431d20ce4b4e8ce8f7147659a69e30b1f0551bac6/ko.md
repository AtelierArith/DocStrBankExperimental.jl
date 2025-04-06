```
push_refspecs(rmt::GitRemote) -> Vector{String}
```

지정된 `rmt`에 대한 *push* refspecs를 가져옵니다. 이 refspecs는 어떤 브랜치를 푸시할지에 대한 정보를 포함합니다.

# 예제

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> close(remote);

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```

```
add_push!(repo::GitRepo, rmt::GitRemote, push_spec::String)
```

지정된 `rmt`에 대한 *push* refspec을 추가합니다. 이 refspec은 어떤 브랜치를 푸시할지에 대한 정보를 포함합니다.

# 예제

```julia-repl
julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, branch);

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```

!!! note
    푸시 refspec을 업데이트한 후 변경 사항이 적용되고 [`push`](@ref) 호출이 작동하려면 해당 `GitRemote`를 [`close`](@ref)하고 다시 열어야 할 수 있습니다.


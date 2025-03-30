```
add_fetch!(repo::GitRepo, rmt::GitRemote, fetch_spec::String)
```

지정된 `rmt`에 대한 *fetch* refspec을 추가합니다. 이 refspec은 어떤 브랜치를 가져올지에 대한 정보를 포함합니다.

# 예제

```julia-repl
julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```

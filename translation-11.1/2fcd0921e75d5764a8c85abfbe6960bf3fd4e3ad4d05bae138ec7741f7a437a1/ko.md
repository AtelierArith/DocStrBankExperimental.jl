```
name(rmt::GitRemote)
```

원격 저장소의 이름을 가져옵니다. 예를 들어 `"origin"`입니다. 만약 원격이 익명인 경우 ( [`GitRemoteAnon`](@ref) 참조) 이름은 빈 문자열 `""`이 됩니다.

# 예제

```julia-repl
julia> repo_url = "https://github.com/JuliaLang/Example.jl";

julia> repo = LibGit2.clone(cache_repo, "test_directory");

julia> remote = LibGit2.GitRemote(repo, "origin", repo_url);

julia> name(remote)
"origin"
```

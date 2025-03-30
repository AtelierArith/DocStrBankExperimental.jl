```
set_remote_url(repo::GitRepo, remote_name, url)
set_remote_url(repo::String, remote_name, url)
```

`remote_name`에 대한 fetch 및 push `url`을 [`GitRepo`](@ref) 또는 `path`에 위치한 git 저장소에 설정합니다. 일반적으로 git 저장소는 원격 이름으로 `"origin"`을 사용합니다.

# 예제

```julia
repo_path = joinpath(tempdir(), "Example")
repo = LibGit2.init(repo_path)
LibGit2.set_remote_url(repo, "upstream", "https://github.com/JuliaLang/Example.jl")
LibGit2.set_remote_url(repo_path, "upstream2", "https://github.com/JuliaLang/Example2.jl")
```

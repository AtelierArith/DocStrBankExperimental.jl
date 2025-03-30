```
set_remote_url(repo::GitRepo, remote_name, url)
set_remote_url(repo::String, remote_name, url)
```

为 [`GitRepo`](@ref) 或位于 `path` 的 git 仓库设置 `remote_name` 的获取和推送 `url`。通常 git 仓库使用 `"origin"` 作为远程名称。

# 示例

```julia
repo_path = joinpath(tempdir(), "Example")
repo = LibGit2.init(repo_path)
LibGit2.set_remote_url(repo, "upstream", "https://github.com/JuliaLang/Example.jl")
LibGit2.set_remote_url(repo_path, "upstream2", "https://github.com/JuliaLang/Example2.jl")
```

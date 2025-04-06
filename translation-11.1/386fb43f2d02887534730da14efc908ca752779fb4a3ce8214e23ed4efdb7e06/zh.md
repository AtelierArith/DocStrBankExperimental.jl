```
clone(repo_url::AbstractString, repo_path::AbstractString, clone_opts::CloneOptions)
```

将远程仓库 `repo_url`（可以是远程 URL 或本地文件系统上的路径）克隆到 `repo_path`（必须是本地文件系统上的路径）。克隆的选项，例如是否执行裸克隆，由 [`CloneOptions`](@ref) 设置。

# 示例

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo = LibGit2.clone(repo_url, "/home/me/projects/Example")
```

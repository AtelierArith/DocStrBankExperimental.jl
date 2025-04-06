```
clone(repo_url::AbstractString, repo_path::AbstractString; kwargs...)
```

将位于 `repo_url` 的远程仓库克隆到本地文件系统位置 `repo_path`。

关键字参数包括：

  * `branch::AbstractString=""`：要克隆的远程分支，如果不是默认的仓库分支（通常是 `master`）。
  * `isbare::Bool=false`：如果为 `true`，则将远程克隆为裸仓库，这将使 `repo_path` 本身成为 git 目录，而不是 `repo_path/.git`。这意味着无法检出工作树。相当于 git CLI 参数 `--bare`。
  * `remote_cb::Ptr{Cvoid}=C_NULL`：在克隆之前用于创建远程的回调。如果为 `C_NULL`（默认值），则不会尝试创建远程 - 将假定其已存在。
  * `credentials::Creds=nothing`：在对私有仓库进行身份验证时提供凭据和/或设置。
  * `callbacks::Callbacks=Callbacks()`：用户提供的回调和有效负载。

等同于 `git clone [-b <branch>] [--bare] <repo_url> <repo_path>`。

# 示例

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo1 = LibGit2.clone(repo_url, "test_path")
repo2 = LibGit2.clone(repo_url, "test_path", isbare=true)
julia_url = "https://github.com/JuliaLang/julia"
julia_repo = LibGit2.clone(julia_url, "julia_path", branch="release-0.6")
```

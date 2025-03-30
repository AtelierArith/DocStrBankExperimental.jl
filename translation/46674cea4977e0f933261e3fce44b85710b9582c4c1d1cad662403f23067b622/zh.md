```
GitRemoteAnon(repo::GitRepo, url::AbstractString) -> GitRemote
```

仅使用其 URL 而不是名称查找远程 git 存储库。

# 示例

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemoteAnon(repo, repo_url)
```

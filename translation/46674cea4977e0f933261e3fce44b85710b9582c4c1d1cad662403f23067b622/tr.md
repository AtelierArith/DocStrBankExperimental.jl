```
GitRemoteAnon(repo::GitRepo, url::AbstractString) -> GitRemote
```

Sadece URL'sini kullanarak bir uzak git deposunu arayın, adını değil.

# Örnekler

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemoteAnon(repo, repo_url)
```

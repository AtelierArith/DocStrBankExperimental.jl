```
GitRemoteAnon(repo::GitRepo, url::AbstractString) -> GitRemote
```

Suchen Sie ein entferntes Git-Repository nur mit seiner URL, nicht mit seinem Namen.

# Beispiele

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemoteAnon(repo, repo_url)
```

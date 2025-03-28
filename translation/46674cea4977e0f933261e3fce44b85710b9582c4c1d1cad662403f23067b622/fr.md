```
GitRemoteAnon(repo::GitRepo, url::AbstractString) -> GitRemote
```

Recherchez un dépôt git distant en utilisant uniquement son URL, pas son nom.

# Exemples

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemoteAnon(repo, repo_url)
```

```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString) -> GitRemote
```

Recherchez un dépôt git distant en utilisant son nom et son URL. Utilise le refspec de récupération par défaut.

# Exemples

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemote(repo, "upstream", repo_url)
```

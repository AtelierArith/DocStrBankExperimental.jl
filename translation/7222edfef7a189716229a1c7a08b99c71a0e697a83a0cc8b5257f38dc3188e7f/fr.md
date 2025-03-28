```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString, fetch_spec::AbstractString) -> GitRemote
```

Recherchez un dépôt git distant en utilisant le nom et l'URL du dépôt, ainsi que des spécifications sur la façon de récupérer depuis le distant (par exemple, quelle branche distante récupérer).

# Exemples

```julia
repo = LibGit2.init(repo_path)
refspec = "+refs/heads/mybranch:refs/remotes/origin/mybranch"
remote = LibGit2.GitRemote(repo, "upstream", repo_url, refspec)
```

```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString, fetch_spec::AbstractString) -> GitRemote
```

Suchen Sie ein entferntes Git-Repository anhand des Namens und der URL des Repositories sowie der Spezifikationen, wie von dem Remote abgerufen werden soll (z. B. welcher Remote-Zweig abgerufen werden soll).

# Beispiele

```julia
repo = LibGit2.init(repo_path)
refspec = "+refs/heads/mybranch:refs/remotes/origin/mybranch"
remote = LibGit2.GitRemote(repo, "upstream", repo_url, refspec)
```

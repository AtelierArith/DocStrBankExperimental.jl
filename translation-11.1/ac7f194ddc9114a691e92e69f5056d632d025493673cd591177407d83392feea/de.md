```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString) -> GitRemote
```

Suchen Sie ein entferntes Git-Repository anhand seines Namens und seiner URL. Verwendet die Standard-Fetch-Refspec.

# Beispiele

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemote(repo, "upstream", repo_url)
```

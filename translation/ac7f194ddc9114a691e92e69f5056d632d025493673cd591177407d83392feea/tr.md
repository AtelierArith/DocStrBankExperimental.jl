```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString) -> GitRemote
```

Bir uzak git deposunu adını ve URL'sini kullanarak arayın. Varsayılan fetch refspec'ini kullanır.

# Örnekler

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemote(repo, "upstream", repo_url)
```

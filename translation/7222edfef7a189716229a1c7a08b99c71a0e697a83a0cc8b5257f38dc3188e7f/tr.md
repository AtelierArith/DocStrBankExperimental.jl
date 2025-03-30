```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString, fetch_spec::AbstractString) -> GitRemote
```

Bir uzak git deposunu, deponun adı ve URL'si ile birlikte, uzaktan nasıl alınacağına dair spesifikasyonlarla (örneğin, hangi uzak dalın alınacağı) arayın.

# Örnekler

```julia
repo = LibGit2.init(repo_path)
refspec = "+refs/heads/mybranch:refs/remotes/origin/mybranch"
remote = LibGit2.GitRemote(repo, "upstream", repo_url, refspec)
```

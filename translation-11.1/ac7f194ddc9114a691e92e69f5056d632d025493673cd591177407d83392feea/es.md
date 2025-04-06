```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString) -> GitRemote
```

Busca un repositorio git remoto utilizando su nombre y URL. Utiliza el refspec de fetch por defecto.

# Ejemplos

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemote(repo, "upstream", repo_url)
```

```
GitRemote(repo::GitRepo, rmt_name::AbstractString, rmt_url::AbstractString, fetch_spec::AbstractString) -> GitRemote
```

Busca un repositorio git remoto utilizando el nombre y la URL del repositorio, así como especificaciones sobre cómo obtener del remoto (por ejemplo, qué rama remota obtener).

# Ejemplos

```julia
repo = LibGit2.init(repo_path)
refspec = "+refs/heads/mybranch:refs/remotes/origin/mybranch"
remote = LibGit2.GitRemote(repo, "upstream", repo_url, refspec)
```

```
GitRemoteAnon(repo::GitRepo, url::AbstractString) -> GitRemote
```

Busca un repositorio git remoto utilizando solo su URL, no su nombre.

# Ejemplos

```julia
repo = LibGit2.init(repo_path)
remote = LibGit2.GitRemoteAnon(repo, repo_url)
```

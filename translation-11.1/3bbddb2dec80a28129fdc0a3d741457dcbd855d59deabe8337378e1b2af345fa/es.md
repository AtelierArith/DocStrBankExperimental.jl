```
set_remote_url(repo::GitRepo, remote_name, url)
set_remote_url(repo::String, remote_name, url)
```

Establece tanto la `url` de fetch como la de push para `remote_name` para el [`GitRepo`](@ref) o el repositorio git ubicado en `path`. Típicamente, los repositorios git utilizan `"origin"` como el nombre remoto.

# Ejemplos

```julia
repo_path = joinpath(tempdir(), "Example")
repo = LibGit2.init(repo_path)
LibGit2.set_remote_url(repo, "upstream", "https://github.com/JuliaLang/Example.jl")
LibGit2.set_remote_url(repo_path, "upstream2", "https://github.com/JuliaLang/Example2.jl")
```

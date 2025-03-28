```
clone(repo_url::AbstractString, repo_path::AbstractString; kwargs...)
```

Clona un repositorio remoto ubicado en `repo_url` a la ubicación del sistema de archivos local `repo_path`.

Los argumentos de palabra clave son:

  * `branch::AbstractString=""`: qué rama del remoto clonar, si no es la rama predeterminada del repositorio (generalmente `master`).
  * `isbare::Bool=false`: si es `true`, clona el remoto como un repositorio bare, lo que hará que `repo_path` sea el directorio git en lugar de `repo_path/.git`. Esto significa que no se puede extraer un árbol de trabajo. Juega el papel del argumento de la CLI de git `--bare`.
  * `remote_cb::Ptr{Cvoid}=C_NULL`: un callback que se utilizará para crear el remoto antes de que se clone. Si es `C_NULL` (el predeterminado), no se intentará crear el remoto; se asumirá que ya existe.
  * `credentials::Creds=nothing`: proporciona credenciales y/o configuraciones al autenticar contra un repositorio privado.
  * `callbacks::Callbacks=Callbacks()`: callbacks y cargas útiles proporcionadas por el usuario.

Equivalente a `git clone [-b <branch>] [--bare] <repo_url> <repo_path>`.

# Ejemplos

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo1 = LibGit2.clone(repo_url, "test_path")
repo2 = LibGit2.clone(repo_url, "test_path", isbare=true)
julia_url = "https://github.com/JuliaLang/julia"
julia_repo = LibGit2.clone(julia_url, "julia_path", branch="release-0.6")
```

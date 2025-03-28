```
clone(repo_url::AbstractString, repo_path::AbstractString; kwargs...)
```

Klonen Sie ein entferntes Repository, das sich unter `repo_url` befindet, in den lokalen Dateispeicherort `repo_path`.

Die Schlüsselwortargumente sind:

  * `branch::AbstractString=""`: welcher Branch des Remotes geklont werden soll, wenn nicht der Standard-Repository-Branch (normalerweise `master`).
  * `isbare::Bool=false`: wenn `true`, klonen Sie das Remote als ein Bare-Repository, was bedeutet, dass `repo_path` selbst das Git-Verzeichnis anstelle von `repo_path/.git` sein wird. Das bedeutet, dass kein Arbeitsbaum ausgecheckt werden kann. Spielt die Rolle des Git-CLI-Arguments `--bare`.
  * `remote_cb::Ptr{Cvoid}=C_NULL`: ein Callback, das verwendet wird, um das Remote zu erstellen, bevor es geklont wird. Wenn `C_NULL` (der Standard), wird kein Versuch unternommen, das Remote zu erstellen - es wird angenommen, dass es bereits existiert.
  * `credentials::Creds=nothing`: bietet Anmeldeinformationen und/oder Einstellungen beim Authentifizieren gegen ein privates Repository.
  * `callbacks::Callbacks=Callbacks()`: vom Benutzer bereitgestellte Callbacks und Payloads.

Entspricht `git clone [-b <branch>] [--bare] <repo_url> <repo_path>`.

# Beispiele

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo1 = LibGit2.clone(repo_url, "test_path")
repo2 = LibGit2.clone(repo_url, "test_path", isbare=true)
julia_url = "https://github.com/JuliaLang/julia"
julia_repo = LibGit2.clone(julia_url, "julia_path", branch="release-0.6")
```

```
LibGit2.isdirty(repo::GitRepo, pathspecs::AbstractString=""; cached::Bool=false) -> Bool
```

Überprüfen, ob es Änderungen an verfolgten Dateien im Arbeitsbaum gegeben hat (wenn `cached=false`) oder im Index (wenn `cached=true`). `pathspecs` sind die Spezifikationen für Optionen für den Diff.

# Beispiele

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdirty(repo) # sollte false sein
open(joinpath(repo_path, new_file), "a") do f
    println(f, "hier ist meine coole neue Datei")
end
LibGit2.isdirty(repo) # jetzt true
LibGit2.isdirty(repo, new_file) # jetzt true
```

Entspricht `git diff-index HEAD [-- <pathspecs>]`. ```

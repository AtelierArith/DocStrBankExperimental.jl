```
LibGit2.isdiff(repo::GitRepo, treeish::AbstractString, pathspecs::AbstractString=""; cached::Bool=false)
```

Überprüft, ob es Unterschiede zwischen dem durch `treeish` angegebenen Baum und den verfolgten Dateien im Arbeitsbaum (wenn `cached=false`) oder im Index (wenn `cached=true`) gibt. `pathspecs` sind die Spezifikationen für Optionen für den Diff.

# Beispiele

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdiff(repo, "HEAD") # sollte false sein
open(joinpath(repo_path, new_file), "a") do f
    println(f, "hier ist meine coole neue Datei")
end
LibGit2.isdiff(repo, "HEAD") # jetzt true
```

Entspricht `git diff-index <treeish> [-- <pathspecs>]`.

```
LibGit2.init(path::AbstractString, bare::Bool=false) -> GitRepo
```

Öffnen Sie ein neues Git-Repository unter `path`. Wenn `bare` `false` ist, wird der Arbeitsbaum in `path/.git` erstellt. Wenn `bare` `true` ist, wird kein Arbeitsverzeichnis erstellt.

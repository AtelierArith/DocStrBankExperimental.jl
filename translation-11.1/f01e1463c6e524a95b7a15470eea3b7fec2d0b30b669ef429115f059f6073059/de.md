```
LibGit2.status(repo::GitRepo, path::String) -> Union{Cuint, Cvoid}
```

Überprüfen Sie den Status der Datei unter `path` im Git-Repository `repo`. Zum Beispiel kann dies verwendet werden, um zu überprüfen, ob die Datei unter `path` geändert wurde und gestaged und committet werden muss.

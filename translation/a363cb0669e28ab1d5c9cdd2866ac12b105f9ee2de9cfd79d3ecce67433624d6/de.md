```
LibGit2.GitStatus(repo::GitRepo; status_opts=StatusOptions())
```

Sammeln Sie Informationen über den Status jeder Datei im Git-Repository `repo` (z. B. ob die Datei geändert, gestaged usw. ist). `status_opts` kann verwendet werden, um verschiedene Optionen festzulegen, zum Beispiel, ob untracked Dateien betrachtet werden sollen oder ob Submodule einbezogen werden sollen oder nicht. Siehe [`StatusOptions`](@ref) für weitere Informationen.

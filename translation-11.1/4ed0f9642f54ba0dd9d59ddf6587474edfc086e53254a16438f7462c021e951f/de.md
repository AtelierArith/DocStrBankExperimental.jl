```
LibGit2.workdir(repo::GitRepo)
```

Gibt den Speicherort des Arbeitsverzeichnisses von `repo` zurück. Dies wird einen Fehler für nackte Repositories auslösen.

!!! Hinweis     Dies ist typischerweise das übergeordnete Verzeichnis von `gitdir(repo)`, kann aber in einigen Fällen unterschiedlich sein: z. B. wenn entweder die Konfigurationsvariable `core.worktree` oder die Umgebungsvariable `GIT_WORK_TREE` gesetzt ist.

Siehe auch [`gitdir`](@ref), [`path`](@ref).

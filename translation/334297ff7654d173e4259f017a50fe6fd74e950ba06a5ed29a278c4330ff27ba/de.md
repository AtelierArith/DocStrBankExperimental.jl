```
LibGit2.path(repo::GitRepo)
```

Gibt den Basisdateipfad des Repositories `repo` zurück.

  * Für normale Repositories ist dies typischerweise das übergeordnete Verzeichnis des ".git"-Verzeichnisses (Hinweis: Dies kann sich vom Arbeitsverzeichnis unterscheiden, siehe `workdir` für weitere Details).
  * Für bare Repositories ist dies der Speicherort der "git"-Dateien.

Siehe auch [`gitdir`](@ref), [`workdir`](@ref).

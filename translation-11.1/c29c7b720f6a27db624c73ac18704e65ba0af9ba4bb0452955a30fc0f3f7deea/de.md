```
GitBlame(repo::GitRepo, path::AbstractString; options::BlameOptions=BlameOptions())
```

Konstruiere ein `GitBlame`-Objekt für die Datei unter `path`, wobei Änderungsinformationen aus der Historie von `repo` verwendet werden. Das `GitBlame`-Objekt zeichnet auf, wer welche Teile der Datei wann und wie geändert hat. `options` steuert, wie der Inhalt der Datei getrennt wird und welche Commits untersucht werden sollen - siehe [`BlameOptions`](@ref) für weitere Informationen.

```
update!(repo::GitRepo, files::AbstractString...)
update!(idx::GitIndex, files::AbstractString...)
```

Aktualisiere alle Dateien mit den durch `files` angegebenen Pfaden im Index `idx` (oder im Index des `repo`). Vergleiche den Zustand jeder Datei im Index mit dem aktuellen Zustand auf der Festplatte, entferne sie, wenn sie auf der Festplatte gelöscht wurde, oder aktualisiere ihren Eintrag in der Objektdatenbank.

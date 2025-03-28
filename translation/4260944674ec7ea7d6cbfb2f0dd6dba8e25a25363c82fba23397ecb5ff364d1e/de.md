```
merge_base(repo::GitRepo, one::AbstractString, two::AbstractString) -> GitHash
```

Finde einen Merge-Basis (einen gemeinsamen Vorfahren) zwischen den Commits `one` und `two`. `one` und `two` können beide in String-Form vorliegen. Gib den `GitHash` der Merge-Basis zurück.

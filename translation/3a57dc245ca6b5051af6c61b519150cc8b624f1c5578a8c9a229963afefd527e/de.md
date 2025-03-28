```
transact(f::Function, repo::GitRepo)
```

Wenden Sie die Funktion `f` auf das Git-Repository `repo` an, indem Sie einen [`snapshot`](@ref) erstellen, bevor Sie `f` anwenden. Wenn ein Fehler innerhalb von `f` auftritt, wird `repo` in seinen Snapshot-Zustand zurückversetzt, indem [`restore`](@ref) verwendet wird. Der aufgetretene Fehler wird erneut ausgelöst, aber der Zustand von `repo` wird nicht beschädigt.

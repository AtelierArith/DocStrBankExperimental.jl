```
restore(s::State, repo::GitRepo)
```

Stellt ein Repository `repo` auf einen vorherigen `State` `s` zurück, zum Beispiel den HEAD eines Branches vor einem Merge-Versuch. `s` kann mit der [`snapshot`](@ref) Funktion generiert werden.

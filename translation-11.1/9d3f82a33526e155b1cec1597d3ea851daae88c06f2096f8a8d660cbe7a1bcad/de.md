```
snapshot(repo::GitRepo) -> State
```

Nehmen Sie einen Snapshot des aktuellen Zustands des Repositories `repo`, indem Sie den aktuellen HEAD, den Index und alle nicht festgeschriebenen Arbeiten speichern. Der Ausgabe `State` kann später während eines Aufrufs von [`restore`](@ref) verwendet werden, um das Repository in den gesnapshotteten Zustand zurückzubringen.

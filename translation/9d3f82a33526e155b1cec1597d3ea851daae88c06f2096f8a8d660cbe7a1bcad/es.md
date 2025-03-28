```
snapshot(repo::GitRepo) -> State
```

Toma una instantánea del estado actual del repositorio `repo`, almacenando el HEAD actual, el índice y cualquier trabajo no confirmado. La salida `State` se puede usar más tarde durante una llamada a [`restore`](@ref) para devolver el repositorio al estado instantáneo.

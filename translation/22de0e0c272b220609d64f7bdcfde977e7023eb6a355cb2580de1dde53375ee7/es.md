```
restore(s::State, repo::GitRepo)
```

Devuelve un repositorio `repo` a un `State` `s` anterior, por ejemplo, el HEAD de una rama antes de un intento de fusión. `s` se puede generar utilizando la función [`snapshot`](@ref).

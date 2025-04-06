```
transact(f::Function, repo::GitRepo)
```

Aplica la función `f` al repositorio git `repo`, tomando un [`snapshot`](@ref) antes de aplicar `f`. Si ocurre un error dentro de `f`, `repo` se devolverá a su estado de snapshot utilizando [`restore`](@ref). El error que ocurrió será lanzado de nuevo, pero el estado de `repo` no se verá corrompido.

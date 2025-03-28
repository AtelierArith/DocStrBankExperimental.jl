```
merge_base(repo::GitRepo, one::AbstractString, two::AbstractString) -> GitHash
```

Encuentra una base de fusión (un ancestro común) entre los commits `one` y `two`. `one` y `two` pueden estar en forma de cadena. Devuelve el `GitHash` de la base de fusión.

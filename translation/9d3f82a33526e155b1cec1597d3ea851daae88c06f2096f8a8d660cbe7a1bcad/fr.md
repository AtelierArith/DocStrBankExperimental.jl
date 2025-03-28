```
snapshot(repo::GitRepo) -> State
```

Prenez un instantané de l'état actuel du dépôt `repo`, en stockant le HEAD actuel, l'index et tout travail non validé. La sortie `State` peut être utilisée plus tard lors d'un appel à [`restore`](@ref) pour ramener le dépôt à l'état instantané.

```
LibGit2.read_tree!(idx::GitIndex, tree::GitTree)
LibGit2.read_tree!(idx::GitIndex, treehash::AbstractGitHash)
```

Lee el árbol `tree` (o el árbol apuntado por `treehash` en el repositorio perteneciente a `idx`) en el índice `idx`. El contenido actual del índice será reemplazado.

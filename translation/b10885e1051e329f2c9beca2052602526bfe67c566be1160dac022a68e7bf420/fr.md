```
LibGit2.read_tree!(idx::GitIndex, tree::GitTree)
LibGit2.read_tree!(idx::GitIndex, treehash::AbstractGitHash)
```

Lire l'arbre `tree` (ou l'arbre pointé par `treehash` dans le dépôt appartenant à `idx`) dans l'index `idx`. Le contenu actuel de l'index sera remplacé.

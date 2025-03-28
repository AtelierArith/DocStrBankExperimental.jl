```
realpath(path::AbstractString) -> String
```

Canonicaliser un chemin en développant les liens symboliques et en supprimant les entrées "." et "..". Sur les systèmes de fichiers insensibles à la casse et préservant la casse (typiquement Mac et Windows), la casse stockée par le système de fichiers pour le chemin est renvoyée.

(Cette fonction lance une exception si `path` n'existe pas dans le système de fichiers.)

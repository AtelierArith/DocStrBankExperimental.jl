```
splitdrive(path::AbstractString) -> (AbstractString, AbstractString)
```

Sur Windows, divise un chemin en la partie de la lettre de lecteur et la partie du chemin. Sur les systèmes Unix, le premier composant est toujours la chaîne vide.

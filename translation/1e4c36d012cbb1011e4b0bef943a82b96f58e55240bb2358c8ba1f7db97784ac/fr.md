```
relpath(path::AbstractString, startpath::AbstractString = ".") -> String
```

Renvoie un chemin de fichier relatif à `path` soit depuis le répertoire actuel, soit depuis un répertoire de départ optionnel. Il s'agit d'un calcul de chemin : le système de fichiers n'est pas accédé pour confirmer l'existence ou la nature de `path` ou `startpath`.

Sous Windows, la sensibilité à la casse est appliquée à chaque partie du chemin sauf pour les lettres de lecteur. Si `path` et `startpath` se réfèrent à des lecteurs différents, le chemin absolu de `path` est renvoyé.

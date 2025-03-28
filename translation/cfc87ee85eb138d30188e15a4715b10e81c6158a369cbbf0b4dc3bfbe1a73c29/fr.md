```
symlink(target::AbstractString, link::AbstractString; dir_target = false)
```

Crée un lien symbolique vers `target` avec le nom `link`.

Sous Windows, les liens symboliques doivent être explicitement déclarés comme se référant à un répertoire ou non. Si `target` existe déjà, par défaut le type de `link` sera détecté automatiquement, cependant si `target` n'existe pas, cette fonction crée par défaut un lien symbolique de fichier à moins que `dir_target` ne soit défini sur `true`. Notez que si l'utilisateur définit `dir_target` mais que `target` existe et est un fichier, un lien symbolique de répertoire sera tout de même créé, mais la désignation du lien symbolique échouera, tout comme si l'utilisateur crée un lien symbolique de fichier (en appelant `symlink()` avec `dir_target` défini sur `false` avant que le répertoire ne soit créé) et essaie de le désigner vers un répertoire.

De plus, il existe deux méthodes pour créer un lien sous Windows : les liens symboliques et les points de jonction. Les points de jonction sont légèrement plus efficaces, mais ne prennent pas en charge les chemins relatifs, donc si un lien symbolique de répertoire relatif est demandé (comme indiqué par `isabspath(target)` retournant `false`), un lien symbolique sera utilisé, sinon un point de jonction sera utilisé. La meilleure pratique pour créer des liens symboliques sous Windows est de les créer uniquement après que les fichiers/répertoires auxquels ils font référence ont déjà été créés.

Voir aussi : [`hardlink`](@ref).

!!! note
    Cette fonction génère une erreur sous les systèmes d'exploitation qui ne prennent pas en charge les liens symboliques doux, tels que Windows XP.


!!! compat "Julia 1.6"
    L'argument clé `dir_target` a été ajouté dans Julia 1.6. Avant cela, les liens symboliques vers des chemins inexistants sur Windows étaient toujours des liens symboliques de fichier, et les liens symboliques relatifs vers des répertoires n'étaient pas pris en charge.


```
artifact_path(hash::SHA1; honor_overrides::Bool=true)
```

Étant donné un artefact (identifié par le hachage d'arbre git SHA1), renvoie son chemin d'installation. Si l'artefact n'existe pas, renvoie l'emplacement où il serait installé.

!!! compat "Julia 1.3"
    Cette fonction nécessite au moins Julia 1.3.


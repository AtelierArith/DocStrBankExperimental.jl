```
artifact_exists(hash::SHA1; honor_overrides::Bool=true)
```

Renvoie si l'artefact donné (identifié par son hash d'arbre git sha1) existe sur le disque. Notez qu'il est possible que l'artefact donné existe à plusieurs emplacements (par exemple, dans plusieurs dépôts).

!!! compat "Julia 1.3"
    Cette fonction nécessite au moins Julia 1.3.


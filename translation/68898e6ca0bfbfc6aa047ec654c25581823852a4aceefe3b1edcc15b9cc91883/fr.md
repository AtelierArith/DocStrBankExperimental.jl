```
message(c::GitCommit, raw::Bool=false)
```

Retourne le message de commit décrivant les changements effectués dans le commit `c`. Si `raw` est `false`, retourne un message légèrement "nettoyé" (qui a toutes les nouvelles lignes en tête supprimées). Si `raw` est `true`, le message n'est pas dépouillé de ces nouvelles lignes.

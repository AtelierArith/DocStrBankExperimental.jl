```
poll_fd(fd, timeout_s::Real=-1; readable=false, writable=false)
```

Surveille un descripteur de fichier `fd` pour des changements dans la disponibilité de lecture ou d'écriture, avec un délai donné par `timeout_s` secondes.

Les arguments de mot-clé déterminent quel statut de lecture et/ou d'écriture doit être surveillé ; au moins l'un d'eux doit être défini sur `true`.

La valeur retournée est un objet avec des champs booléens `readable`, `writable` et `timedout`, donnant le résultat du sondage.

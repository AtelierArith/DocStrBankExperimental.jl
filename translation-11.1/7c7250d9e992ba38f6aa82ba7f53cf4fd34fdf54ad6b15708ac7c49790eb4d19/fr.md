```
open_exclusive(path::String; mode, poll_interval, wait, stale_age, refresh) :: File
```

Créez un nouveau fichier pour un accès exclusif en lecture-écriture. Si `wait` est `false`, alors une erreur se produira si les fichiers de verrouillage existent, sinon, bloquez jusqu'à ce que nous obtenions le verrou.

Pour une description des arguments de mot-clé, voir [`mkpidlock`](@ref).

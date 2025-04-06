```
fetch(rmt::GitRemote, refspecs; options::FetchOptions=FetchOptions(), msg="")
```

Récupérer depuis le dépôt git distant `rmt` spécifié, en utilisant `refspecs` pour déterminer quelle(s) branche(s) distante(s) récupérer. Les arguments de mot-clé sont :

  * `options` : détermine les options pour la récupération, par exemple, s'il faut élaguer par la suite. Voir [`FetchOptions`](@ref) pour plus d'informations.
  * `msg` : un message à insérer dans les reflogs.

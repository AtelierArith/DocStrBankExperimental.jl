```
fetch(repo::GitRepo; kwargs...)
```

Récupère les mises à jour d'un upstream du dépôt `repo`.

Les arguments clés sont :

  * `remote::AbstractString="origin"` : quel remote, spécifié par nom, de `repo` à récupérer. Si cela est vide, l'URL sera utilisée pour construire un remote anonyme.
  * `remoteurl::AbstractString=""` : l'URL de `remote`. Si non spécifié, sera supposé basé sur le nom donné de `remote`.
  * `refspecs=AbstractString[]` : détermine les propriétés de la récupération.
  * `credentials=nothing` : fournit des identifiants et/ou des paramètres lors de l'authentification contre un `remote` privé.
  * `callbacks=Callbacks()` : rappels et charges utiles fournis par l'utilisateur.

Équivalent à `git fetch [<remoteurl>|<repo>] [<refspecs>]`.

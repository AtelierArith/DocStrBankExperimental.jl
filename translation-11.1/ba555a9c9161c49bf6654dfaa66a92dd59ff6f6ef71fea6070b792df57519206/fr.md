```
push(repo::GitRepo; kwargs...)
```

Pousse les mises à jour vers un upstream de `repo`.

Les arguments clés sont :

  * `remote::AbstractString="origin"` : le nom du remote upstream vers lequel pousser.
  * `remoteurl::AbstractString=""` : l'URL de `remote`.
  * `refspecs=AbstractString[]` : détermine les propriétés de la poussée.
  * `force::Bool=false` : détermine si la poussée sera une poussée forcée, écrasant la branche distante.
  * `credentials=nothing` : fournit des identifiants et/ou des paramètres lors de l'authentification contre un `remote` privé.
  * `callbacks=Callbacks()` : rappels et charges utiles fournis par l'utilisateur.

Équivalent à `git push [<remoteurl>|<repo>] [<refspecs>]`.

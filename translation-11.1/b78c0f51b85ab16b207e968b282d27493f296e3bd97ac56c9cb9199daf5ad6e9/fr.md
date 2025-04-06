```
remoteref_id(r::AbstractRemoteRef) -> RRID
```

Les `Future`s et les `RemoteChannel`s sont identifiés par des champs :

  * `where` - fait référence au nœud où l'objet/de stockage sous-jacent auquel la référence fait référence existe réellement.
  * `whence` - fait référence au nœud à partir duquel la référence distante a été créée. Notez que cela est différent du nœud où l'objet sous-jacent auquel il est fait référence existe réellement. Par exemple, appeler `RemoteChannel(2)` depuis le processus maître donnerait une valeur `where` de 2 et une valeur `whence` de 1.
  * `id` est unique parmi toutes les références créées à partir du travailleur spécifié par `whence`.

Ensemble, `whence` et `id` identifient de manière unique une référence parmi tous les travailleurs.

`remoteref_id` est une API de bas niveau qui renvoie un objet `RRID` qui encapsule les valeurs `whence` et `id` d'une référence distante.

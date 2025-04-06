```
push(rmt::GitRemote, refspecs; force::Bool=false, options::PushOptions=PushOptions())
```

Poussez vers le dépôt git distant `rmt` spécifié, en utilisant `refspecs` pour déterminer quelle(s) branche(s) distante(s) pousser. Les arguments clés sont :

  * `force` : si `true`, un push forcé se produira, ignorant les conflits.
  * `options` : détermine les options pour le push, par exemple, quels en-têtes de proxy utiliser. Voir [`PushOptions`](@ref) pour plus d'informations.

!!! note
    Vous pouvez ajouter des informations sur les refspecs de push de deux autres manières : en définissant une option dans le `GitConfig` du dépôt (avec `push.default` comme clé) ou en appelant [`add_push!`](@ref). Sinon, vous devrez spécifier explicitement un refspec de push dans l'appel à `push` pour qu'il ait un effet, comme ceci : `LibGit2.push(repo, refspecs=["refs/heads/master"])`.


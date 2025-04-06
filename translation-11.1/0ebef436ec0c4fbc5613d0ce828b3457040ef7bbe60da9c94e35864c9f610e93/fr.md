```
LibGit2.FetchOptions
```

Correspond à la structure [`git_fetch_options`](https://libgit2.org/libgit2/#HEAD/type/git_fetch_options).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `callbacks` : rappels distants à utiliser pendant le fetch.
  * `prune` : s'il faut effectuer un prune après le fetch ou non. La valeur par défaut est d'utiliser le paramètre du `GitConfig`.
  * `update_fetchhead` : s'il faut mettre à jour le [`FetchHead`](@ref) après le fetch. La valeur par défaut est d'effectuer la mise à jour, ce qui est le comportement normal de git.
  * `download_tags` : s'il faut télécharger les tags présents sur le distant ou non. La valeur par défaut est de demander les tags pour les objets qui sont de toute façon téléchargés depuis le serveur.
  * `proxy_opts` : options pour se connecter au distant via un proxy. Voir [`ProxyOptions`](@ref). Présent uniquement sur les versions de libgit2 supérieures ou égales à 0.25.0.
  * `custom_headers` : tous les en-têtes supplémentaires nécessaires pour le fetch. Présent uniquement sur les versions de libgit2 supérieures ou égales à 0.24.0.

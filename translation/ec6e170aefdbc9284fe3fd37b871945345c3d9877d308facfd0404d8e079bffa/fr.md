```
LibGit2.ProxyOptions
```

Options pour se connecter via un proxy.

Correspond à la structure [`git_proxy_options`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_options).

Les champs représentent :

  * `version` : version de la structure utilisée, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `proxytype` : un `enum` pour le type de proxy à utiliser. Défini dans [`git_proxy_t`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_t). L'énumération Julia correspondante est `GIT_PROXY` et a les valeurs :

      * `PROXY_NONE` : ne pas tenter la connexion via un proxy.
      * `PROXY_AUTO` : tenter de déterminer la configuration du proxy à partir de la configuration git.
      * `PROXY_SPECIFIED` : se connecter en utilisant l'URL donnée dans le champ `url` de cette structure.

    Par défaut, il s'agit de détecter automatiquement le type de proxy.
  * `url` : l'URL du proxy.
  * `credential_cb` : un pointeur vers une fonction de rappel qui sera appelée si le distant nécessite une authentification pour se connecter.
  * `certificate_cb` : un pointeur vers une fonction de rappel qui sera appelée si la vérification du certificat échoue. Cela permet à l'utilisateur de décider s'il souhaite ou non continuer la connexion. Si la fonction retourne `1`, la connexion sera autorisée. Si elle retourne `0`, la connexion ne sera pas autorisée. Une valeur négative peut être utilisée pour retourner des erreurs.
  * `payload` : la charge utile à fournir aux deux fonctions de rappel.

# Exemples

```julia-repl
julia> fo = LibGit2.FetchOptions(
           proxy_opts = LibGit2.ProxyOptions(url = Cstring("https://my_proxy_url.com")))

julia> fetch(remote, "master", options=fo)
```

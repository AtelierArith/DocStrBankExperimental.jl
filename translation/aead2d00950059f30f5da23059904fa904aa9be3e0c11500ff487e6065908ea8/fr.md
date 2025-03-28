```
LibGit2.PushOptions
```

Correspond à la structure [`git_push_options`](https://libgit2.org/libgit2/#HEAD/type/git_push_options).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `parallelism` : si un fichier pack doit être créé, cette variable définit le nombre de threads de travail qui seront lancés par le packbuilder. Si `0`, le packbuilder définira automatiquement le nombre de threads à utiliser. La valeur par défaut est `1`.
  * `callbacks` : les callbacks (par exemple, pour l'authentification avec le distant) à utiliser pour le push.
  * `proxy_opts` : uniquement pertinent si la version de LibGit2 est supérieure ou égale à `0.25.0`. Définit les options pour utiliser un proxy pour communiquer avec un distant. Voir [`ProxyOptions`](@ref) pour plus d'informations.
  * `custom_headers` : uniquement pertinent si la version de LibGit2 est supérieure ou égale à `0.24.0`. En-têtes supplémentaires nécessaires pour l'opération de push.

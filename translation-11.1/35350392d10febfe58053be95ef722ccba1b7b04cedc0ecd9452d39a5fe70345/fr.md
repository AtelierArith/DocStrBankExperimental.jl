```
LibGit2.CheckoutOptions
```

Correspond à la structure [`git_checkout_options`](https://libgit2.org/libgit2/#HEAD/type/git_checkout_options).

Les champs représentent :

  * `version` : version de la structure utilisée, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `checkout_strategy` : détermine comment gérer les conflits et si le checkout/recréer des fichiers manquants doit être forcé.
  * `disable_filters` : si non nul, n'applique pas de filtres comme CLRF (pour convertir les nouvelles lignes de fichiers entre UNIX et DOS).
  * `dir_mode` : mode de lecture/écriture/accès pour tous les répertoires impliqués dans le checkout. Par défaut, c'est `0755`.
  * `file_mode` : mode de lecture/écriture/accès pour tous les fichiers impliqués dans le checkout. Par défaut, c'est `0755` ou `0644`, selon le blob.
  * `file_open_flags` : drapeaux utilisés pour ouvrir des fichiers pendant le checkout.
  * `notify_flags` : Drapeaux pour quel type de conflits l'utilisateur doit être informé.
  * `notify_cb` : Une fonction de rappel optionnelle pour notifier l'utilisateur si un conflit de checkout se produit. Si cette fonction retourne une valeur non nulle, le checkout sera annulé.
  * `notify_payload` : Charge utile pour la fonction de rappel de notification.
  * `progress_cb` : Une fonction de rappel optionnelle pour afficher la progression du checkout.
  * `progress_payload` : Charge utile pour le rappel de progression.
  * `paths` : Si non vide, décrit quels chemins rechercher pendant le checkout. Si vide, le checkout se produira sur tous les fichiers du dépôt.
  * `baseline` : Contenu attendu du [`workdir`](@ref), capturé dans un (pointeur vers un) [`GitTree`](@ref). Par défaut, c'est l'état de l'arbre à HEAD.
  * `baseline_index` : Contenu attendu du [`workdir`](@ref), capturé dans un (pointeur vers un) `GitIndex`. Par défaut, c'est l'état de l'index à HEAD.
  * `target_directory` : Si non vide, checkout dans ce répertoire au lieu du `workdir`.
  * `ancestor_label` : En cas de conflits, le nom du côté ancêtre commun.
  * `our_label` : En cas de conflits, le nom de notre côté.
  * `their_label` : En cas de conflits, le nom de leur côté.
  * `perfdata_cb` : Une fonction de rappel optionnelle pour afficher les données de performance.
  * `perfdata_payload` : Charge utile pour le rappel de performance.

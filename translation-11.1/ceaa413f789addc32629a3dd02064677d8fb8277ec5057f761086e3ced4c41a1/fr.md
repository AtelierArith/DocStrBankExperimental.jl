```
LibGit2.RebaseOptions
```

Correspond à la structure `git_rebase_options`.

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `quiet` : informer les autres clients git aidant avec/travaillant sur le rebase que le rebase doit être effectué "silencieusement". Utilisé pour l'interopérabilité. La valeur par défaut est `1`.
  * `inmemory` : démarrer un rebase en mémoire. Les appelants travaillant sur le rebase peuvent passer par ses étapes et valider les modifications, mais ne peuvent pas revenir en arrière sur HEAD ou mettre à jour le dépôt. Le [`workdir`](@ref) ne sera pas modifié. Présent uniquement sur les versions de libgit2 supérieures ou égales à 0.24.0.
  * `rewrite_notes_ref` : nom de la référence aux notes à utiliser pour réécrire les notes de commit à la fin du rebase.
  * `merge_opts` : options de fusion contrôlant comment les arbres seront fusionnés à chaque étape du rebase. Présent uniquement sur les versions de libgit2 supérieures ou égales à 0.24.0.
  * `checkout_opts` : options de checkout pour écrire des fichiers lors de l'initialisation du rebase, en le parcourant et en l'abandonnant. Voir [`CheckoutOptions`](@ref) pour plus d'informations.

```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}, fastforward::Bool; kwargs...) -> Bool
```

Fusionner les modifications des commits annotés (capturés en tant qu'objets [`GitAnnotated`](@ref)) `anns` dans le HEAD du dépôt `repo`. Si `fastforward` est `true`, *seule* une fusion fastforward est autorisée. Dans ce cas, si des conflits se produisent, la fusion échouera. Sinon, si `fastforward` est `false`, la fusion peut produire un fichier de conflit que l'utilisateur devra résoudre.

Les arguments de mot-clé sont :

  * `merge_opts::MergeOptions = MergeOptions()`: options pour la manière de réaliser la fusion, y compris si le fastforward est autorisé. Voir [`MergeOptions`](@ref) pour plus d'informations.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: options pour la manière de réaliser le checkout. Voir [`CheckoutOptions`](@ref) pour plus d'informations.

`anns` peut faire référence à des têtes de branches distantes ou locales. Retourne `true` si la fusion est réussie, sinon retourne `false` (par exemple, si aucune fusion n'est possible car les branches n'ont pas d'ancêtre commun).

# Exemples

```julia
upst_ann_1 = LibGit2.GitAnnotated(repo, "branch/a")

# fusionner la branche, fastforward
LibGit2.merge!(repo, [upst_ann_1], true)

# conflits de fusion !
upst_ann_2 = LibGit2.GitAnnotated(repo, "branch/b")
# fusionner la branche, essayer de fastforward
LibGit2.merge!(repo, [upst_ann_2], true) # retournera false
LibGit2.merge!(repo, [upst_ann_2], false) # retournera true
```

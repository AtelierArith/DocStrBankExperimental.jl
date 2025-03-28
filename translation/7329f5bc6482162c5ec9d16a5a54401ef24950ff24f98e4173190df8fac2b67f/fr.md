```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}; kwargs...) -> Bool
```

Fusionner les modifications des commits annotés (capturés en tant qu'objets [`GitAnnotated`](@ref)) `anns` dans le HEAD du dépôt `repo`. Les arguments de mot-clé sont :

  * `merge_opts::MergeOptions = MergeOptions()`: options pour la façon de réaliser la fusion, y compris si le fastforward est autorisé. Voir [`MergeOptions`](@ref) pour plus d'informations.
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: options pour la façon de réaliser le checkout. Voir [`CheckoutOptions`](@ref) pour plus d'informations.

`anns` peut faire référence à des têtes de branches distantes ou locales. Retourne `true` si la fusion est réussie, sinon retourne `false` (par exemple, si aucune fusion n'est possible car les branches n'ont pas d'ancêtre commun).

# Exemples

```julia
upst_ann = LibGit2.GitAnnotated(repo, "branch/a")

# fusionner la branche
LibGit2.merge!(repo, [upst_ann])
```

```
merge!(repo::GitRepo; kwargs...) -> Bool
```

Effectuez une fusion git sur le dépôt `repo`, fusionnant les commits avec un historique divergent dans la branche actuelle. Retourne `true` si la fusion a réussi, `false` sinon.

Les arguments de mot-clé sont :

  * `committish::AbstractString=""` : Fusionnez le(s) commit(s) nommé(s) dans `committish`.
  * `branch::AbstractString=""` : Fusionnez la branche `branch` et tous ses commits depuis qu'elle a divergé de la branche actuelle.
  * `fastforward::Bool=false` : Si `fastforward` est `true`, ne fusionnez que si la fusion est un fast-forward (le head de la branche actuelle est un ancêtre des commits à fusionner), sinon refusez de fusionner et retournez `false`. Cela équivaut à l'option CLI git `--ff-only`.
  * `merge_opts::MergeOptions=MergeOptions()` : `merge_opts` spécifie les options pour la fusion, telles que la stratégie de fusion en cas de conflits.
  * `checkout_opts::CheckoutOptions=CheckoutOptions()` : `checkout_opts` spécifie les options pour l'étape de checkout.

Équivalent à `git merge [--ff-only] [<committish> | <branch>]`.

!!! note
    Si vous spécifiez une `branch`, cela doit être fait au format de référence, car la chaîne sera transformée en un `GitReference`. Par exemple, si vous souhaitez fusionner la branche `branch_a`, vous appelleriez `merge!(repo, branch="refs/heads/branch_a")`.


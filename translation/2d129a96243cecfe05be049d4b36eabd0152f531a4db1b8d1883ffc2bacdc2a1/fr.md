```
finish(ts::AbstractTestSet)
```

Effectuez tout traitement final nécessaire pour le testset donné. Cela est appelé par l'infrastructure `@testset` après l'exécution d'un bloc de test.

Les sous-types `AbstractTestSet` personnalisés doivent appeler `record` sur leur parent (s'il y en a un) pour s'ajouter à l'arbre des résultats de test. Cela pourrait être implémenté comme suit :

```julia
if get_testset_depth() != 0
    # Attacher ce test set au test set parent
    parent_ts = get_testset()
    record(parent_ts, self)
    return self
end
```

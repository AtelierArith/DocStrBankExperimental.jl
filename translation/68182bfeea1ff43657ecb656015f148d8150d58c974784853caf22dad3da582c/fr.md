```
Sampler(rng, x, repetition = Val(Inf))
```

Retourne un objet sampler qui peut être utilisé pour générer des valeurs aléatoires à partir de `rng` pour `x`.

Lorsque `sp = Sampler(rng, x, repetition)`, `rand(rng, sp)` sera utilisé pour tirer des valeurs aléatoires, et devrait être défini en conséquence.

`repetition` peut être `Val(1)` ou `Val(Inf)`, et devrait être utilisé comme une suggestion pour décider de la quantité de pré-calcul, si applicable.

[`Random.SamplerType`](@ref) et [`Random.SamplerTrivial`](@ref) sont des solutions par défaut pour *types* et *valeurs*, respectivement. [`Random.SamplerSimple`](@ref) peut être utilisé pour stocker des valeurs pré-calculées sans définir des types supplémentaires uniquement à cette fin.

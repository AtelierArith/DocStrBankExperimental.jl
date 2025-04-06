```
Random.default_rng() -> rng
```

Renvoie le générateur de nombres aléatoires (RNG) global par défaut, qui est utilisé par les fonctions liées à `rand` lorsque aucun RNG explicite n'est fourni.

Lorsque le module `Random` est chargé, le RNG par défaut est *aléatoirement* initialisé, via [`Random.seed!()`](@ref) : cela signifie qu'à chaque fois qu'une nouvelle session julia est démarrée, le premier appel à `rand()` produit un résultat différent, à moins que `seed!(seed)` ne soit appelé en premier.

Il est thread-safe : des threads distincts peuvent appeler en toute sécurité des fonctions liées à `rand` sur `default_rng()` de manière concurrente, par exemple `rand(default_rng())`.

!!! note
    Le type du RNG par défaut est un détail d'implémentation. À travers différentes versions de Julia, vous ne devez pas vous attendre à ce que le RNG par défaut ait toujours le même type, ni qu'il produise le même flux de nombres aléatoires pour une graine donnée.


!!! compat "Julia 1.3"
    Cette fonction a été introduite dans Julia 1.3.


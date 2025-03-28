```
LinearAlgebra.peakflops(n::Integer=4096; eltype::DataType=Float64, ntrials::Integer=3, parallel::Bool=false)
```

`peakflops` calcule le taux de flop maximal de l'ordinateur en utilisant la précision double [`gemm!`](@ref LinearAlgebra.BLAS.gemm!). Par défaut, si aucun argument n'est spécifié, il multiplie deux matrices `Float64` de taille `n x n`, où `n = 4096`. Si le BLAS sous-jacent utilise plusieurs threads, des taux de flop plus élevés sont réalisés. Le nombre de threads BLAS peut être défini avec [`BLAS.set_num_threads(n)`](@ref).

Si l'argument clé `eltype` est fourni, `peakflops` construira des matrices avec des éléments de type `eltype` pour calculer le taux de flop maximal.

Par défaut, `peakflops` utilisera le meilleur timing parmi 3 essais. Si l'argument clé `ntrials` est fourni, `peakflops` utilisera ce nombre d'essais pour choisir le meilleur timing.

Si l'argument clé `parallel` est défini sur `true`, `peakflops` est exécuté en parallèle sur tous les processeurs de travail. Le taux de flop de l'ensemble de l'ordinateur parallèle est retourné. Lors de l'exécution en parallèle, un seul thread BLAS est utilisé. L'argument `n` fait toujours référence à la taille du problème qui est résolu sur chaque processeur.

!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1. Dans Julia 1.0, elle est disponible dans la bibliothèque standard `InteractiveUtils`.


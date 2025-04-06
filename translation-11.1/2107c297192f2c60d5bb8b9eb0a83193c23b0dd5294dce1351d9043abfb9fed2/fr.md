# Parallel Computing

Julia prend en charge ces quatre catégories de programmation concurrente et parallèle :

1. **Tâches "asynchrones", ou coroutines** :

    Les tâches Julia permettent de suspendre et de reprendre des calculs pour les E/S, la gestion d'événements, les processus producteurs-consommateurs et des modèles similaires. Les tâches peuvent se synchroniser par des opérations comme [`wait`](@ref) et [`fetch`](@ref), et communiquer via [`Channel`](@ref)s. Bien qu'elles ne soient pas strictement du calcul parallèle en elles-mêmes, Julia vous permet de planifier des [`Task`](@ref)s sur plusieurs threads.
2. **Multi-threading**:

    La [multi-threading](@ref man-multithreading) de Julia offre la possibilité de planifier des tâches simultanément sur plus d'un thread ou cœur de CPU, partageant la mémoire. C'est généralement le moyen le plus simple d'obtenir du parallélisme sur son PC ou sur un grand serveur multi-cœurs unique. Le multi-threading de Julia est composable. Lorsqu'une fonction multi-threadée appelle une autre fonction multi-threadée, Julia planifiera tous les threads globalement sur les ressources disponibles, sans surabonnement.
3. **Informatique distribuée**:

    L'informatique distribuée exécute plusieurs processus Julia avec des espaces mémoire séparés. Ceux-ci peuvent être sur le même ordinateur ou sur plusieurs ordinateurs. La bibliothèque standard [`Distributed`](@ref man-distributed) offre la capacité d'exécution à distance d'une fonction Julia. Avec ce bloc de construction de base, il est possible de créer de nombreux types d'abstractions d'informatique distribuée. Des packages comme [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) sont un exemple de ce type d'abstraction. D'autre part, des packages comme [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) et [`Elemental.jl`](https://github.com/JuliaParallel/Elemental.jl) donnent accès à l'écosystème MPI existant de bibliothèques.
4. **Calcul informatique GPU**:

    Le compilateur GPU Julia offre la possibilité d'exécuter du code Julia nativement sur des GPU. Il existe un riche écosystème de packages Julia qui ciblent les GPU. Le site [JuliaGPU.org](https://juliagpu.org) fournit une liste des capacités, des GPU pris en charge, des packages connexes et de la documentation.

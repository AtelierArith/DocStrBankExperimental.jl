```
addprocs(manager::ClusterManager; kwargs...) -> Liste des identifiants de processus
```

Lance des processus de travail via le gestionnaire de cluster spécifié.

Par exemple, les clusters Beowulf sont pris en charge via un gestionnaire de cluster personnalisé implémenté dans le package `ClusterManagers.jl`.

Le nombre de secondes qu'un nouveau travailleur attend pour établir une connexion avec le maître peut être spécifié via la variable `JULIA_WORKER_TIMEOUT` dans l'environnement du processus de travailleur. Pertinent uniquement lors de l'utilisation de TCP/IP comme transport.

Pour lancer des travailleurs sans bloquer le REPL, ou la fonction contenant si vous lancez des travailleurs de manière programmatique, exécutez `addprocs` dans sa propre tâche.

# Exemples

```julia
# Sur des clusters occupés, appelez `addprocs` de manière asynchrone
t = @async addprocs(...)
```

```julia
# Utilisez les travailleurs au fur et à mesure qu'ils se connectent
if nprocs() > 1   # Assurez-vous qu'au moins un nouveau travailleur est disponible
   ....   # effectuez une exécution distribuée
end
```

```julia
# Récupérez les ID des travailleurs nouvellement lancés, ou tout message d'erreur
if istaskdone(t)   # Vérifiez si `addprocs` a été complété pour s'assurer que `fetch` ne bloque pas
    if nworkers() == N
        new_pids = fetch(t)
    else
        fetch(t)
    end
end
```

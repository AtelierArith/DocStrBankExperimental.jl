```
addprocs(np::Integer=Sys.CPU_THREADS; restrict=true, kwargs...) -> Liste des identifiants de processus
```

Lancez des travailleurs `np` sur l'hôte local en utilisant le `LocalManager` intégré.

Les travailleurs locaux héritent de l'environnement de package actuel (c'est-à-dire le projet actif, [`LOAD_PATH`](@ref), et [`DEPOT_PATH`](@ref)) du processus principal.

!!! warning
    Notez que les travailleurs n'exécutent pas de script de démarrage `~/.julia/config/startup.jl`, ni ne synchronisent leur état global (tel que les options de ligne de commande, les variables globales, les définitions de nouvelles méthodes et les modules chargés) avec aucun des autres processus en cours d'exécution.


**Arguments clés** :

  * `restrict::Bool` : si `true` (par défaut), la liaison est restreinte à `127.0.0.1`.
  * `dir`, `exename`, `exeflags`, `env`, `topology`, `lazy`, `enable_threaded_blas` : même effet que pour `SSHManager`, voir la documentation pour [`addprocs(machines::AbstractVector)`](@ref).

!!! compat "Julia 1.9"
    L'héritage de l'environnement de package et l'argument clé `env` ont été ajoutés dans Julia 1.9.


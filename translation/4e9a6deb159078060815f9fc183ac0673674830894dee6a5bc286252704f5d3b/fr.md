```
WorkerConfig
```

Type utilisé par [`ClusterManager`](@ref)s pour contrôler les travailleurs ajoutés à leurs clusters. Certains champs sont utilisés par tous les gestionnaires de clusters pour accéder à un hôte :

  * `io` – la connexion utilisée pour accéder au travailleur (un sous-type de `IO` ou `Nothing`)
  * `host` – l'adresse de l'hôte (soit une `String` ou `Nothing`)
  * `port` – le port sur l'hôte utilisé pour se connecter au travailleur (soit un `Int` ou `Nothing`)

Certains sont utilisés par le gestionnaire de cluster pour ajouter des travailleurs à un hôte déjà initialisé :

  * `count` – le nombre de travailleurs à lancer sur l'hôte
  * `exename` – le chemin vers l'exécutable Julia sur l'hôte, par défaut `"$(Sys.BINDIR)/julia"` ou `"$(Sys.BINDIR)/julia-debug"`
  * `exeflags` – options à utiliser lors du lancement de Julia à distance

Le champ `userdata` est utilisé pour stocker des informations pour chaque travailleur par des gestionnaires externes.

Certains champs sont utilisés par `SSHManager` et des gestionnaires similaires :

  * `tunnel` – `true` (utiliser le tunneling), `false` (ne pas utiliser le tunneling), ou [`nothing`](@ref) (utiliser la valeur par défaut pour le gestionnaire)
  * `multiplex` – `true` (utiliser le multiplexage SSH pour le tunneling) ou `false`
  * `forward` – l'option de transfert utilisée pour l'option `-L` de ssh
  * `bind_addr` – l'adresse sur l'hôte distant à laquelle se lier
  * `sshflags` – options à utiliser pour établir la connexion SSH
  * `max_parallel` – le nombre maximum de travailleurs à connecter en parallèle sur l'hôte

Certains champs sont utilisés à la fois par les `LocalManager`s et les `SSHManager`s :

  * `connect_at` – détermine s'il s'agit d'un appel de configuration travailleur-à-travailleur ou pilote-à-travailleur
  * `process` – le processus qui sera connecté (généralement le gestionnaire assignera cela lors de [`addprocs`](@ref))
  * `ospid` – l'ID de processus selon le système d'exploitation de l'hôte, utilisé pour interrompre les processus des travailleurs
  * `environ` – dictionnaire privé utilisé pour stocker des informations temporaires par les gestionnaires Local/SSH
  * `ident` – travailleur tel qu'identifié par le [`ClusterManager`](@ref)
  * `connect_idents` – liste des identifiants de travailleurs auxquels le travailleur doit se connecter s'il utilise une topologie personnalisée
  * `enable_threaded_blas` – `true`, `false`, ou `nothing`, s'il faut utiliser BLAS multithreadé ou non sur les travailleurs

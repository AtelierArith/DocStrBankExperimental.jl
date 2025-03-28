```
connect(manager::ClusterManager, pid::Int, config::WorkerConfig) -> (instrm::IO, outstrm::IO)
```

Implémenté par des gestionnaires de cluster utilisant des transports personnalisés. Cela doit établir une connexion logique avec le travailleur ayant l'identifiant `pid`, spécifié par `config`, et retourner une paire d'objets `IO`. Les messages de `pid` vers le processus actuel seront lus à partir de `instrm`, tandis que les messages à envoyer à `pid` seront écrits dans `outstrm`. L'implémentation du transport personnalisé doit garantir que les messages sont livrés et reçus complètement et dans l'ordre. `connect(manager::ClusterManager.....)` configure des connexions de socket TCP/IP entre les travailleurs.

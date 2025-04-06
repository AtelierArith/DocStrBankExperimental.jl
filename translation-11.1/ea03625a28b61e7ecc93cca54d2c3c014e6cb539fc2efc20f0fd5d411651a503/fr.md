```
addprocs(machines; tunnel=false, sshflags=``, max_parallel=10, kwargs...) -> Liste des identifiants de processus
```

Ajoutez des processus de travail sur des machines distantes via SSH. La configuration se fait avec des arguments de mots-clés (voir ci-dessous). En particulier, le mot-clé `exename` peut être utilisé pour spécifier le chemin vers le binaire `julia` sur la ou les machines distantes.

`machines` est un vecteur de "spécifications de machine" qui sont données sous forme de chaînes du type `[user@]host[:port] [bind_addr[:port]]`. `user` par défaut est l'utilisateur actuel et `port` le port SSH standard. Si `[bind_addr[:port]]` est spécifié, d'autres travailleurs se connecteront à ce travailleur à l'adresse `bind_addr` et au port spécifiés.

Il est possible de lancer plusieurs processus sur un hôte distant en utilisant un tuple dans le vecteur `machines` ou la forme `(machine_spec, count)`, où `count` est le nombre de travailleurs à lancer sur l'hôte spécifié. Passer `:auto` comme nombre de travailleurs lancera autant de travailleurs que le nombre de threads CPU sur l'hôte distant.

**Exemples**:

```julia
addprocs([
    "remote1",               # un travailleur sur 'remote1' se connectant avec le nom d'utilisateur actuel
    "user@remote2",          # un travailleur sur 'remote2' se connectant avec le nom d'utilisateur 'user'
    "user@remote3:2222",     # spécifiant le port SSH à '2222' pour 'remote3'
    ("user@remote4", 4),     # lancer 4 travailleurs sur 'remote4'
    ("user@remote5", :auto), # lancer autant de travailleurs que de threads CPU sur 'remote5'
])
```

**Arguments de mots-clés**:

  * `tunnel`: si `true`, alors un tunnel SSH sera utilisé pour se connecter au travailleur depuis le processus maître. Par défaut, c'est `false`.
  * `multiplex`: si `true`, alors le multiplexage SSH est utilisé pour le tunnel SSH. Par défaut, c'est `false`.
  * `ssh`: le nom ou le chemin de l'exécutable du client SSH utilisé pour démarrer les travailleurs. Par défaut, c'est `"ssh"`.
  * `sshflags`: spécifie des options ssh supplémentaires, par exemple ```sshflags=`-i /home/foo/bar.pem` ```
  * `max_parallel`: spécifie le nombre maximum de travailleurs connectés en parallèle à un hôte. Par défaut, c'est 10.
  * `shell`: spécifie le type de shell auquel ssh se connecte sur les travailleurs.

      * `shell=:posix`: un shell Unix/Linux compatible POSIX (sh, ksh, bash, dash, zsh, etc.). Par défaut.
      * `shell=:csh`: un shell C Unix (csh, tcsh).
      * `shell=:wincmd`: Microsoft Windows `cmd.exe`.
  * `dir`: spécifie le répertoire de travail sur les travailleurs. Par défaut, c'est le répertoire actuel de l'hôte (tel que trouvé par `pwd()`)
  * `enable_threaded_blas`: si `true`, alors BLAS s'exécutera sur plusieurs threads dans les processus ajoutés. Par défaut, c'est `false`.
  * `exename`: nom de l'exécutable `julia`. Par défaut, c'est `"$(Sys.BINDIR)/julia"` ou `"$(Sys.BINDIR)/julia-debug"` selon le cas. Il est recommandé d'utiliser une version commune de Julia sur toutes les machines distantes car la sérialisation et la distribution de code pourraient échouer sinon.
  * `exeflags`: drapeaux supplémentaires passés aux processus de travail.
  * `topology`: Spécifie comment les travailleurs se connectent les uns aux autres. L'envoi d'un message entre des travailleurs non connectés entraîne une erreur.

      * `topology=:all_to_all`: Tous les processus sont connectés les uns aux autres. Par défaut.
      * `topology=:master_worker`: Seul le processus pilote, c'est-à-dire `pid` 1 se connecte aux travailleurs. Les travailleurs ne se connectent pas entre eux.
      * `topology=:custom`: La méthode `launch` du gestionnaire de cluster spécifie la topologie de connexion via les champs `ident` et `connect_idents` dans `WorkerConfig`. Un travailleur avec une identité de gestionnaire de cluster `ident` se connectera à tous les travailleurs spécifiés dans `connect_idents`.
  * `lazy`: Applicable uniquement avec `topology=:all_to_all`. Si `true`, les connexions travailleur-travailleur sont configurées de manière paresseuse, c'est-à-dire qu'elles sont configurées lors de la première instance d'un appel distant entre travailleurs. Par défaut, c'est vrai.
  * `env`: fournir un tableau de paires de chaînes telles que `env=["JULIA_DEPOT_PATH"=>"/depot"]` pour demander que des variables d'environnement soient définies sur la machine distante. Par défaut, seule la variable d'environnement `JULIA_WORKER_TIMEOUT` est passée automatiquement de l'environnement local à l'environnement distant.
  * `cmdline_cookie`: passez le cookie d'authentification via l'option de ligne de commande `--worker`. Le comportement par défaut (plus sécurisé) de passer le cookie via ssh stdio peut se bloquer avec des travailleurs Windows utilisant des versions Julia ou Windows plus anciennes (avant ConPTY), auquel cas `cmdline_cookie=true` offre une solution de contournement.

!!! compat "Julia 1.6"
    Les arguments de mots-clés `ssh`, `shell`, `env` et `cmdline_cookie` ont été ajoutés dans Julia 1.6.


Variables d'environnement:

Si le processus maître échoue à établir une connexion avec un travailleur nouvellement lancé dans les 60,0 secondes, le travailleur considère cela comme une situation fatale et se termine. Ce délai peut être contrôlé via la variable d'environnement `JULIA_WORKER_TIMEOUT`. La valeur de `JULIA_WORKER_TIMEOUT` sur le processus maître spécifie le nombre de secondes qu'un travailleur nouvellement lancé attend pour établir une connexion.

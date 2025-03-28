# Environment Variables

Julia peut être configuré avec un certain nombre de variables d'environnement, définies soit de la manière habituelle pour chaque système d'exploitation, soit de manière portable depuis Julia. Supposons que vous souhaitiez définir la variable d'environnement [`JULIA_EDITOR`](@ref JULIA_EDITOR) à `vim`, vous pouvez taper `ENV["JULIA_EDITOR"] = "vim"` (par exemple, dans le REPL) pour effectuer ce changement au cas par cas, ou ajouter la même chose au fichier de configuration utilisateur `~/.julia/config/startup.jl` dans le répertoire personnel de l'utilisateur pour avoir un effet permanent. La valeur actuelle de la même variable d'environnement peut être déterminée en évaluant `ENV["JULIA_EDITOR"]`.

Les variables d'environnement que Julia utilise commencent généralement par `JULIA`. Si [`InteractiveUtils.versioninfo`](@ref) est appelé avec le mot-clé `verbose=true`, alors la sortie listera toutes les variables d'environnement définies pertinentes pour Julia, y compris celles qui incluent `JULIA` dans leurs noms.

!!! note
    Il est recommandé d'éviter de modifier les variables d'environnement pendant l'exécution, par exemple dans un `~/.julia/config/startup.jl`.

    Une raison est que certaines variables du langage julia, telles que [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) et [`JULIA_PROJECT`](@ref JULIA_PROJECT), doivent être définies avant le démarrage de Julia.

    De même, les fonctions `__init__()` des modules utilisateur dans l'image système (via PackageCompiler) sont exécutées avant `startup.jl`, donc définir des variables d'environnement dans un `startup.jl` peut être trop tard pour le code utilisateur.

    De plus, modifier les variables d'environnement pendant l'exécution peut introduire des conditions de concurrence dans un code autrement inoffensif.

    Dans Bash, les variables d'environnement peuvent être définies manuellement en exécutant, par exemple, `export JULIA_NUM_THREADS=4` avant de démarrer Julia, ou en ajoutant la même commande à `~/.bashrc` ou `~/.bash_profile` pour définir la variable chaque fois que Bash est démarré.


## File locations

### [`JULIA_BINDIR`](@id JULIA_BINDIR)

Le chemin absolu du répertoire contenant l'exécutable Julia, qui définit la variable globale [`Sys.BINDIR`](@ref). Si `$JULIA_BINDIR` n'est pas défini, alors Julia détermine la valeur de `Sys.BINDIR` au moment de l'exécution.

L'exécutable lui-même est l'un des

```
$JULIA_BINDIR/julia
$JULIA_BINDIR/julia-debug
```

par défaut.

La variable globale `Base.DATAROOTDIR` détermine un chemin relatif depuis `Sys.BINDIR` vers le répertoire de données associé à Julia. Ensuite, le chemin

```
$JULIA_BINDIR/$DATAROOTDIR/julia/base
```

détermine le répertoire dans lequel Julia recherche initialement les fichiers source (via `Base.find_source_file()`).

De même, la variable globale `Base.SYSCONFDIR` détermine un chemin relatif vers le répertoire du fichier de configuration. Ensuite, Julia recherche un fichier `startup.jl` à

```
$JULIA_BINDIR/$SYSCONFDIR/julia/startup.jl
$JULIA_BINDIR/../etc/julia/startup.jl
```

par défaut (via `Base.load_julia_startup()`).

Par exemple, une installation Linux avec un exécutable Julia situé à `/bin/julia`, un `DATAROOTDIR` de `../share`, et un `SYSCONFDIR` de `../etc` aura [`JULIA_BINDIR`](@ref JULIA_BINDIR) défini sur `/bin`, un chemin de recherche de fichiers source de

```
/share/julia/base
```

et un chemin de recherche de configuration global de

```
/etc/julia/startup.jl
```

### [`JULIA_PROJECT`](@id JULIA_PROJECT)

Un chemin de répertoire qui indique quel projet doit être le projet actif initial. Définir cette variable d'environnement a le même effet que de spécifier l'option de démarrage `--project`, mais `--project` a une priorité plus élevée. Si la variable est définie sur `@.` (notez le point final), alors Julia essaie de trouver un répertoire de projet qui contient un fichier `Project.toml` ou `JuliaProject.toml` à partir du répertoire actuel et de ses parents. Voir aussi le chapitre sur [Code Loading](@ref code-loading).

!!! note
    [`JULIA_PROJECT`](@ref JULIA_PROJECT) doit être défini avant de commencer julia ; le définir dans `startup.jl` est trop tard dans le processus de démarrage.


### [`JULIA_LOAD_PATH`](@id JULIA_LOAD_PATH)

La variable d'environnement [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) est utilisée pour peupler la variable globale Julia [`LOAD_PATH`](@ref), qui détermine quels paquets peuvent être chargés via `import` et `using` (voir [Code Loading](@ref code-loading)).

Contrairement à la variable `PATH` du shell, les entrées vides dans [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) sont étendues à la valeur par défaut de `LOAD_PATH`, `["@", "@v#.#", "@stdlib"]` lors de la population de `LOAD_PATH`. Cela permet d'ajouter, de préfixer, etc. la valeur du chemin de chargement dans les scripts shell, peu importe si `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` est déjà défini ou non. Par exemple, pour préfixer le répertoire `/foo/bar` à `LOAD_PATH`, il suffit de faire

```sh
export JULIA_LOAD_PATH="/foo/bar:$JULIA_LOAD_PATH"
```

Si la variable d'environnement [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) est déjà définie, sa valeur ancienne sera préfixée par `/foo/bar`. D'autre part, si `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` n'est pas définie, alors elle sera définie sur `/foo/bar:` ce qui se développera en une valeur `LOAD_PATH` de `["/foo/bar", "@", "@v#.#", "@stdlib"]`. Si `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` est définie sur la chaîne vide, elle se développe en un tableau `LOAD_PATH` vide. En d'autres termes, la chaîne vide est interprétée comme un tableau à zéro élément, et non comme un tableau à un élément contenant la chaîne vide. Ce comportement a été choisi afin qu'il soit possible de définir un chemin de chargement vide via la variable d'environnement. Si vous souhaitez le chemin de chargement par défaut, soit vous supprimez la variable d'environnement, soit si elle doit avoir une valeur, définissez-la sur la chaîne `:`.

!!! note
    Sur Windows, les éléments de chemin sont séparés par le caractère `;`, comme c'est le cas pour la plupart des listes de chemins sur Windows. Remplacez `:` par `;` dans le paragraphe ci-dessus.


### [`JULIA_DEPOT_PATH`](@id JULIA_DEPOT_PATH)

La variable d'environnement [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) est utilisée pour peupler la variable globale Julia [`DEPOT_PATH`](@ref), qui contrôle où le gestionnaire de paquets, ainsi que les mécanismes de chargement de code de Julia, recherchent les registres de paquets, les paquets installés, les environnements nommés, les clones de dépôts, les images de paquets compilés mises en cache, les fichiers de configuration et l'emplacement par défaut du fichier d'historique du REPL.

Contrairement à la variable `PATH` du shell mais similaire à [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH), les entrées vides dans [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) ont un comportement spécial :

  * À la fin, il est étendu à la valeur par défaut de `DEPOT_PATH`, *excluant* le dépôt de l'utilisateur.
  * Au départ, il est étendu à la valeur par défaut de `DEPOT_PATH`, *y compris* le dépôt de l'utilisateur.

Cela permet de remplacer facilement le dépôt utilisateur, tout en conservant l'accès aux ressources qui sont regroupées avec Julia, comme les fichiers de cache, les artefacts, etc. Par exemple, pour changer le dépôt utilisateur en `/foo/bar`, utilisez un `:` à la fin.

```sh
export JULIA_DEPOT_PATH="/foo/bar:"
```

Toutes les opérations de paquet, comme le clonage des registres ou l'installation de paquets, écriront désormais dans `/foo/bar`, mais comme l'entrée vide est étendue au dépôt système par défaut, toutes les ressources regroupées seront toujours disponibles. Si vous souhaitez vraiment utiliser uniquement le dépôt à `/foo/bar`, et ne pas charger de ressources regroupées, il suffit de définir la variable d'environnement sur `/foo/bar` sans le deux-points final.

Pour ajouter un dépôt à la fin de la liste par défaut complète, y compris le dépôt utilisateur par défaut, utilisez un `:` en tête.

```sh
export JULIA_DEPOT_PATH=":/foo/bar"
```

Il y a deux exceptions à la règle ci-dessus. Premièrement, si [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) est défini comme une chaîne vide, il s'étend à un tableau `DEPOT_PATH` vide. En d'autres termes, la chaîne vide est interprétée comme un tableau à zéro élément, et non comme un tableau à un élément contenant la chaîne vide. Ce comportement a été choisi afin qu'il soit possible de définir un chemin de dépôt vide via la variable d'environnement.

Deuxièmement, si aucun dépôt utilisateur n'est spécifié dans [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH), alors l'entrée vide est étendue au dépôt par défaut *y compris* le dépôt utilisateur. Cela permet d'utiliser le dépôt par défaut, comme si la variable d'environnement n'était pas définie, en la définissant sur la chaîne `:`.

!!! note
    Sur Windows, les éléments de chemin sont séparés par le caractère `;`, comme c'est le cas pour la plupart des listes de chemins sur Windows. Remplacez `:` par `;` dans le paragraphe ci-dessus.


!!! note
    [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) doit être défini avant de commencer julia ; le définir dans `startup.jl` est trop tard dans le processus de démarrage ; à ce moment-là, vous pouvez plutôt modifier directement le tableau `DEPOT_PATH`, qui est peuplé à partir de la variable d'environnement.


### [`JULIA_HISTORY`](@id JULIA_HISTORY)

Le chemin absolu `REPL.find_hist_file()` du fichier d'historique du REPL. Si `$JULIA_HISTORY` n'est pas défini, alors `REPL.find_hist_file()` par défaut à

```
$(DEPOT_PATH[1])/logs/repl_history.jl
```

### [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@id JULIA_MAX_NUM_PRECOMPILE_FILES)

Définit le nombre maximum d'instances différentes d'un seul package qui doivent être stockées dans le cache de précompilation (par défaut = 10).

### [`JULIA_VERBOSE_LINKING`](@id JULIA_VERBOSE_LINKING)

Si défini sur vrai, les commandes de l'éditeur de liens seront affichées pendant la précompilation.

## Pkg.jl

### [`JULIA_CI`](@id JULIA_CI)

Si défini sur `true`, cela indique au serveur de paquets que toutes les opérations de paquets font partie d'un système d'intégration continue (CI) dans le but de recueillir des statistiques d'utilisation des paquets.

### [`JULIA_NUM_PRECOMPILE_TASKS`](@id JULIA_NUM_PRECOMPILE_TASKS)

Le nombre de tâches parallèles à utiliser lors de la précompilation des packages. Voir [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_DEVDIR`](@id JULIA_PKG_DEVDIR)

Le répertoire par défaut utilisé par [`Pkg.develop`](https://pkgdocs.julialang.org/v1/api/#Pkg.develop) pour télécharger des paquets.

### [`JULIA_PKG_IGNORE_HASHES`](@id JULIA_PKG_IGNORE_HASHES)

Si défini sur `1`, cela ignorera les hachages incorrects dans les artefacts. Cela doit être utilisé avec précaution, car cela désactive la vérification des téléchargements, mais peut résoudre des problèmes lors du déplacement de fichiers entre différents types de systèmes de fichiers. Voir [Pkg.jl issue #2317](https://github.com/JuliaLang/Pkg.jl/issues/2317) pour plus de détails.

!!! compat "Julia 1.6"
    Ceci n'est pris en charge qu'à partir de Julia 1.6 et au-dessus.


### [`JULIA_PKG_OFFLINE`](@id JULIA_PKG_OFFLINE)

Si défini sur `true`, cela activera le mode hors ligne : voir [`Pkg.offline`](https://pkgdocs.julialang.org/v1/api/#Pkg.offline).

!!! compat "Julia 1.5"
    Le mode hors ligne de Pkg nécessite Julia 1.5 ou une version ultérieure.


### [`JULIA_PKG_PRECOMPILE_AUTO`](@id JULIA_PKG_PRECOMPILE_AUTO)

Si défini sur `0`, cela désactivera la précompilation automatique par les actions de package qui modifient le manifeste. Voir [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_SERVER`](@id JULIA_PKG_SERVER)

Spécifie l'URL du registre de paquets à utiliser. Par défaut, `Pkg` utilise `https://pkg.julialang.org` pour récupérer les paquets Julia. De plus, vous pouvez désactiver l'utilisation du protocole PkgServer et accéder directement aux paquets depuis leurs hôtes (GitHub, GitLab, etc.) en définissant : `export JULIA_PKG_SERVER=""`

### [`JULIA_PKG_SERVER_REGISTRY_PREFERENCE`](@id JULIA_PKG_SERVER_REGISTRY_PREFERENCE)

Spécifie le type de registre préféré. Les valeurs actuellement prises en charge sont `conservative` (la valeur par défaut), qui ne publiera que les ressources qui ont été traitées par le serveur de stockage (et qui ont donc une probabilité plus élevée d'être disponibles depuis les PkgServers), tandis que `eager` publiera des registres dont les ressources n'ont pas nécessairement été traitées par les serveurs de stockage. Les utilisateurs derrière des pare-feu restrictifs qui n'autorisent pas le téléchargement depuis des serveurs arbitraires ne devraient pas utiliser le type `eager`.

!!! compat "Julia 1.7"
    Cela n'affecte que Julia 1.7 et supérieur.


### [`JULIA_PKG_UNPACK_REGISTRY`](@id JULIA_PKG_UNPACK_REGISTRY)

Si défini sur `true`, cela décompressera le registre au lieu de le stocker sous forme de tarball compressé.

!!! compat "Julia 1.7"
    Cela n'affecte que Julia 1.7 et les versions supérieures. Les versions antérieures décompresseront toujours le registre.


### [`JULIA_PKG_USE_CLI_GIT`](@id JULIA_PKG_USE_CLI_GIT)

Si défini sur `true`, les opérations Pkg qui utilisent le protocole git utiliseront un exécutable `git` externe au lieu de la bibliothèque libgit2 par défaut.

!!! compat "Julia 1.7"
    L'utilisation de l'exécutable `git` n'est prise en charge que sur Julia 1.7 et versions supérieures.


### [`JULIA_PKGRESOLVE_ACCURACY`](@id JULIA_PKGRESOLVE_ACCURACY)

L'exactitude du résolveur de paquets. Cela devrait être un entier positif, la valeur par défaut est `1`.

### [`JULIA_PKG_PRESERVE_TIERED_INSTALLED`](@id JULIA_PKG_PRESERVE_TIERED_INSTALLED)

Changez la stratégie d'installation par défaut des paquets en `Pkg.PRESERVE_TIERED_INSTALLED` pour permettre au gestionnaire de paquets d'essayer d'installer des versions de paquets tout en conservant autant de versions de paquets déjà installées que possible.

!!! compat "Julia 1.9"
    Cela n'affecte que Julia 1.9 et supérieur.


## Network transport

### [`JULIA_NO_VERIFY_HOSTS`](@id JULIA_NO_VERIFY_HOSTS)

### [`JULIA_SSL_NO_VERIFY_HOSTS`](@id JULIA_SSL_NO_VERIFY_HOSTS)

### [`JULIA_SSH_NO_VERIFY_HOSTS`](@id JULIA_SSH_NO_VERIFY_HOSTS)

### [`JULIA_ALWAYS_VERIFY_HOSTS`](@id JULIA_ALWAYS_VERIFY_HOSTS)

Spécifiez les hôtes dont l'identité doit ou ne doit pas être vérifiée pour des couches de transport spécifiques. Voir [`NetworkOptions.verify_host`](https://github.com/JuliaLang/NetworkOptions.jl#verify_host)

### [`JULIA_SSL_CA_ROOTS_PATH`](@id JULIA_SSL_CA_ROOTS_PATH)

Spécifiez le fichier ou le répertoire contenant les racines de l'autorité de certification. Voir [`NetworkOptions.ca_roots`](https://github.com/JuliaLang/NetworkOptions.jl#ca_roots)

## External applications

### [`JULIA_SHELL`](@id JULIA_SHELL)

Le chemin absolu du shell avec lequel Julia doit exécuter des commandes externes (via `Base.repl_cmd()`). Par défaut, il utilise la variable d'environnement `$SHELL`, et revient à `/bin/sh` si `$SHELL` n'est pas défini.

!!! note
    Sur Windows, cette variable d'environnement est ignorée et les commandes externes sont exécutées directement.


### [`JULIA_EDITOR`](@id JULIA_EDITOR)

L'éditeur retourné par `InteractiveUtils.editor()` et utilisé dans, par exemple, [`InteractiveUtils.edit`](@ref), fait référence à la commande de l'éditeur préféré, par exemple `vim`.

`$JULIA_EDITOR` a la priorité sur `$VISUAL`, qui a son tour a la priorité sur `$EDITOR`. Si aucune de ces variables d'environnement n'est définie, l'éditeur est considéré comme `open` sur Windows et OS X, ou `/etc/alternatives/editor` s'il existe, ou `emacs` sinon.

Pour utiliser Visual Studio Code sur Windows, définissez `$JULIA_EDITOR` sur `code.cmd`.

## Parallelization

### [`JULIA_CPU_THREADS`](@id JULIA_CPU_THREADS)

Remplace la variable globale [`Base.Sys.CPU_THREADS`](@ref), le nombre de cœurs CPU logiques disponibles.

### [`JULIA_WORKER_TIMEOUT`](@id JULIA_WORKER_TIMEOUT)

Un [`Float64`](@ref) qui définit la valeur de `Distributed.worker_timeout()` (par défaut : `60.0`). Cette fonction donne le nombre de secondes qu'un processus de travail attendra qu'un processus maître établisse une connexion avant de mourir.

### [`JULIA_NUM_THREADS`](@id JULIA_NUM_THREADS)

Un entier non signé de 64 bits (`uint64_t`) qui définit le nombre maximum de threads disponibles pour Julia. Si `$JULIA_NUM_THREADS` n'est pas positif ou n'est pas défini, ou si le nombre de threads CPU ne peut pas être déterminé par des appels système, alors le nombre de threads est fixé à `1`.

Si `$JULIA_NUM_THREADS` est défini sur `auto`, alors le nombre de threads sera défini sur le nombre de threads CPU.

!!! note
    `JULIA_NUM_THREADS` doit être défini avant de démarrer julia ; le définir dans `startup.jl` est trop tard dans le processus de démarrage.


!!! compat "Julia 1.5"
    Dans Julia 1.5 et versions supérieures, le nombre de threads peut également être spécifié au démarrage en utilisant l'argument de ligne de commande `-t`/`--threads`.


!!! compat "Julia 1.7"
    La valeur `auto` pour `$JULIA_NUM_THREADS` nécessite Julia 1.7 ou une version supérieure.


### [`JULIA_THREAD_SLEEP_THRESHOLD`](@id JULIA_THREAD_SLEEP_THRESHOLD)

Si défini sur une chaîne qui commence par la sous-chaîne insensible à la casse `"infinite"`, alors les threads en rotation ne dorment jamais. Sinon, `$JULIA_THREAD_SLEEP_THRESHOLD` est interprété comme un entier non signé de 64 bits (`uint64_t`) et donne, en nanosecondes, la durée après laquelle les threads en rotation doivent dormir.

### [`JULIA_NUM_GC_THREADS`](@id JULIA_NUM_GC_THREADS)

Définit le nombre de threads utilisés par la collecte des déchets. Si non spécifié, il est fixé à la moitié du nombre de threads de travail.

!!! compat "Julia 1.10"
    La variable d'environnement a été ajoutée dans la version 1.10.


### [`JULIA_IMAGE_THREADS`](@id JULIA_IMAGE_THREADS)

Un entier non signé de 32 bits qui définit le nombre de threads utilisés par la compilation d'images dans ce processus Julia. La valeur de cette variable peut être ignorée si le module est un petit module. Si elle n'est pas spécifiée, la plus petite valeur entre [`JULIA_CPU_THREADS`](@ref JULIA_CPU_THREADS) ou la moitié du nombre de cœurs CPU logiques est utilisée à la place.

### [`JULIA_IMAGE_TIMINGS`](@id JULIA_IMAGE_TIMINGS)

Une valeur booléenne qui détermine si des informations de timing détaillées sont imprimées lors de la compilation de l'image. Par défaut, c'est 0.

### [`JULIA_EXCLUSIVE`](@id JULIA_EXCLUSIVE)

Si défini à autre chose que `0`, alors la politique de thread de Julia est cohérente avec l'exécution sur une machine dédiée : le thread maître est sur le processeur 0, et les threads sont affinitisés. Sinon, Julia laisse le système d'exploitation gérer la politique des threads.

## REPL formatting

Variables d'environnement qui déterminent comment la sortie REPL doit être formatée dans le terminal. En général, ces variables doivent être définies sur [ANSI terminal escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code). Julia fournit une interface de haut niveau avec une grande partie de la même fonctionnalité ; voir la section sur [The Julia REPL](@ref).

### [`JULIA_ERROR_COLOR`](@id JULIA_ERROR_COLOR)

Le formatage `Base.error_color()` (par défaut : rouge clair, `"\033[91m"`) que les erreurs devraient avoir dans le terminal.

### [`JULIA_WARN_COLOR`](@id JULIA_WARN_COLOR)

Le formatage `Base.warn_color()` (par défaut : jaune, `"\033[93m"`) que les avertissements devraient avoir dans le terminal.

### [`JULIA_INFO_COLOR`](@id JULIA_INFO_COLOR)

Le formatage `Base.info_color()` (par défaut : cyan, `"\033[36m"`) que l'info devrait avoir dans le terminal.

### [`JULIA_INPUT_COLOR`](@id JULIA_INPUT_COLOR)

Le formatage `Base.input_color()` (par défaut : normal, `"\033[0m"`) que l'entrée devrait avoir dans le terminal.

### [`JULIA_ANSWER_COLOR`](@id JULIA_ANSWER_COLOR)

Le formatage `Base.answer_color()` (par défaut : normal, `"\033[0m"`) que la sortie devrait avoir dans le terminal.

## System and Package Image Building

### [`JULIA_CPU_TARGET`](@id JULIA_CPU_TARGET)

Modifier l'architecture de la machine cible pour (pré)compiler [system](@ref sysimg-multi-versioning) et [package images](@ref pkgimgs-multi-versioning). `JULIA_CPU_TARGET` n'affecte que la génération d'images de code machine qui sont sorties dans un cache disque. Contrairement à `--cpu-target`, ou `-C`, [command line option](@ref cli), cela n'influence pas la génération de code juste-à-temps (JIT) au sein d'une session Julia où le code machine est uniquement stocké en mémoire.

Les valeurs valides pour [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) peuvent être obtenues en exécutant `julia -C help`.

La configuration [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) est importante pour les systèmes de calcul hétérogènes où des processeurs de types ou de caractéristiques distincts peuvent être présents. Cela est couramment rencontré dans les clusters de calcul haute performance (HPC) puisque les nœuds de composants peuvent utiliser des processeurs distincts.

La chaîne cible du CPU est une liste de chaînes séparées par `;` chaque chaîne commence par un nom de CPU ou d'architecture et est suivie d'une liste facultative de fonctionnalités séparées par `,`. Un nom de CPU `générique` ou vide signifie l'ensemble de fonctionnalités de base requis de l'ISA cible qui est au moins l'architecture avec laquelle le runtime C/C++ est compilé. Chaque chaîne est interprétée par LLVM.

Quelques fonctionnalités spéciales sont prises en charge :

1. `clone_all`

    Cela oblige la cible à avoir toutes les fonctions dans sysimg clonées. Lorsqu'il est utilisé sous forme négative (c'est-à-dire `-clone_all`), cela désactive le clonage complet qui est activé par défaut pour certaines cibles.
2. `base([0-9]*)`

    Cela spécifie l'index de cible de base (basé sur 0). La cible de base est la cible sur laquelle la cible actuelle est basée, c'est-à-dire que les fonctions qui ne sont pas clonées utiliseront la version de la cible de base. Cette option entraîne le clonage complet de la cible de base (comme si `clone_all` était spécifié pour elle) si ce n'est pas la cible par défaut (0). L'index ne peut être que plus petit que l'index actuel.
3. `opt_size`

    Optimisez pour la taille avec un impact minimal sur les performances. `-Os` de Clang/GCC.
4. `min_size`

    Optimisez uniquement pour la taille. `-Oz` de Clang.

## Debugging and profiling

### [`JULIA_DEBUG`](@id JULIA_DEBUG)

Activez la journalisation de débogage pour un fichier ou un module, voir [`Logging`](@ref man-logging) pour plus d'informations.

### [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@id JULIA_PROFILE_PEEK_HEAP_SNAPSHOT)

Activer la collecte d'un instantané de tas pendant l'exécution via le mécanisme de profilage peek. Voir [Triggered During Execution](@ref).

### [`JULIA_TIMING_SUBSYSTEMS`](@id JULIA_TIMING_SUBSYSTEMS)

Vous permet d'activer ou de désactiver des zones pour un exécution spécifique de Julia. Par exemple, définir la variable sur `+GC,-INFERENCE` activera les zones `GC` et désactivera les zones `INFERENCE`. Voir [Dynamically Enabling and Disabling Zones](@ref).

### [`JULIA_GC_ALLOC_POOL`](@id JULIA_GC_ALLOC_POOL)

### [`JULIA_GC_ALLOC_OTHER`](@id JULIA_GC_ALLOC_OTHER)

### [`JULIA_GC_ALLOC_PRINT`](@id JULIA_GC_ALLOC_PRINT)

Si définies, ces variables d'environnement prennent des chaînes qui commencent éventuellement par le caractère `'r'`, suivi d'une interpolation de chaîne d'une liste séparée par des deux-points de trois entiers signés 64 bits (`int64_t`). Ce triplet d'entiers `a:b:c` représente la suite arithmétique `a`, `a + b`, `a + 2*b`, ... `c`.

  * Si c'est la `n`ème fois que `jl_gc_pool_alloc()` a été appelée, et que `n` appartient à la suite arithmétique représentée par `$JULIA_GC_ALLOC_POOL`, alors la collecte des ordures est forcée.
  * Si c'est la `n`ième fois que `maybe_collect()` a été appelée, et que `n` appartient à la suite arithmétique représentée par `$JULIA_GC_ALLOC_OTHER`, alors la collecte des ordures est forcée.
  * Si c'est la `n`ème fois que `jl_gc_collect()` a été appelé, et que `n` appartient à la séquence arithmétique représentée par `$JULIA_GC_ALLOC_PRINT`, alors les comptes pour le nombre d'appels à `jl_gc_pool_alloc()` et `maybe_collect()` sont imprimés.

Si la valeur de la variable d'environnement commence par le caractère `'r'`, alors l'intervalle entre les événements de collecte des ordures est randomisé.

!!! note
    Ces variables d'environnement n'ont d'effet que si Julia a été compilé avec le débogage de la collecte des ordures (c'est-à-dire si `WITH_GC_DEBUG_ENV` est défini sur `1` dans la configuration de construction).


### [`JULIA_GC_NO_GENERATIONAL`](@id JULIA_GC_NO_GENERATIONAL)

Si défini à autre chose que `0`, alors le collecteur de déchets de Julia n'effectue jamais de "balayages rapides" de la mémoire.

!!! note
    Cette variable d'environnement n'a d'effet que si Julia a été compilé avec le débogage de la collecte des ordures (c'est-à-dire si `WITH_GC_DEBUG_ENV` est défini sur `1` dans la configuration de construction).


### [`JULIA_GC_WAIT_FOR_DEBUGGER`](@id JULIA_GC_WAIT_FOR_DEBUGGER)

Si défini à autre chose que `0`, alors le collecteur de déchets Julia attendra qu'un débogueur se connecte au lieu d'abandonner chaque fois qu'il y a une erreur critique.

!!! note
    Cette variable d'environnement n'a d'effet que si Julia a été compilé avec le débogage de la collecte des ordures (c'est-à-dire si `WITH_GC_DEBUG_ENV` est défini sur `1` dans la configuration de construction).


### [`ENABLE_JITPROFILING`](@id ENABLE_JITPROFILING)

Si défini à autre chose que `0`, alors le compilateur créera et enregistrera un écouteur d'événements pour le profilage juste-à-temps (JIT).

!!! note
    Cette variable d'environnement n'a d'effet que si Julia a été compilé avec le support de profilage JIT, en utilisant soit

      * Le [VTune™ Amplifier](https://software.intel.com/en-us/vtune) d'Intel (`USE_INTEL_JITEVENTS` défini sur `1` dans la configuration de construction), ou
      * [OProfile](https://oprofile.sourceforge.io/news/) (`USE_OPROFILE_JITEVENTS` défini sur `1` dans la configuration de construction).
      * [Perf](https://perf.wiki.kernel.org) (`USE_PERF_JITEVENTS` défini sur `1` dans la configuration de construction). Cette intégration est activée par défaut.


### [`ENABLE_GDBLISTENER`](@id ENABLE_GDBLISTENER)

Si défini à autre chose que `0`, cela active l'enregistrement GDB du code Julia sur les versions de production. Sur les versions de débogage de Julia, cela est toujours activé. Il est recommandé de l'utiliser avec `-g 2`.

### [`JULIA_LLVM_ARGS`](@id JULIA_LLVM_ARGS)

Arguments à passer au backend LLVM.

### `JULIA_FALLBACK_REPL`

Force le repl de secours au lieu de REPL.jl.

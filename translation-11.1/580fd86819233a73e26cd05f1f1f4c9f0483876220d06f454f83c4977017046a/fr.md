# [Multi-Threading](@id man-multithreading)

Visitez ce [blog post](https://julialang.org/blog/2019/07/multithreading/) pour une présentation des fonctionnalités de multi-threading de Julia.

## Starting Julia with multiple threads

Par défaut, Julia démarre avec un seul fil d'exécution. Cela peut être vérifié en utilisant la commande [`Threads.nthreads()`](@ref) :

```jldoctest
julia> Threads.nthreads()
1
```

Le nombre de threads d'exécution est contrôlé soit en utilisant l'argument de ligne de commande `-t`/`--threads`, soit en utilisant la variable d'environnement [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS). Lorsque les deux sont spécifiés, alors `-t`/`--threads` a la priorité.

Le nombre de threads peut être spécifié soit comme un entier (`--threads=4`), soit comme `auto` (`--threads=auto`), où `auto` essaie d'inférer un nombre utile de threads à utiliser (voir [Command-line Options](@ref command-line-interface) pour plus de détails).

!!! compat "Julia 1.5"
    L'argument de ligne de commande `-t`/`--threads` nécessite au moins Julia 1.5. Dans les versions antérieures, vous devez utiliser la variable d'environnement à la place.


!!! compat "Julia 1.7"
    Utiliser `auto` comme valeur de la variable d'environnement [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) nécessite au moins Julia 1.7. Dans les versions antérieures, cette valeur est ignorée.


Commençons Julia avec 4 threads :

```bash
$ julia --threads 4
```

Vérifions qu'il y a 4 fils à notre disposition.

```julia-repl
julia> Threads.nthreads()
4
```

Mais nous sommes actuellement sur le fil principal. Pour vérifier, nous utilisons la fonction [`Threads.threadid`](@ref)

```jldoctest
julia> Threads.threadid()
1
```

!!! note
    Si vous préférez utiliser la variable d'environnement, vous pouvez la définir comme suit dans Bash (Linux/macOS) :

    ```bash
    export JULIA_NUM_THREADS=4
    ```

    C shell sur Linux/macOS, CMD sur Windows :

    ```bash
    set JULIA_NUM_THREADS=4
    ```

    Powershell sur Windows :

    ```powershell
    $env:JULIA_NUM_THREADS=4
    ```

    Notez que cela doit être fait *avant* de commencer Julia.


!!! note
    Le nombre de threads spécifié avec `-t`/`--threads` est propagé aux processus de travail qui sont lancés en utilisant les options de ligne de commande `-p`/`--procs` ou `--machine-file`. Par exemple, `julia -p2 -t2` lance 1 processus principal avec 2 processus de travail, et les trois processus ont 2 threads activés. Pour un contrôle plus précis sur les threads de travail, utilisez [`addprocs`](@ref) et passez `-t`/`--threads` comme `exeflags`.


### Multiple GC Threads

Le ramasse-miettes (GC) peut utiliser plusieurs threads. La quantité utilisée est soit la moitié du nombre de threads de travail de calcul, soit configurée par l'argument de ligne de commande `--gcthreads` ou en utilisant la variable d'environnement [`JULIA_NUM_GC_THREADS`](@ref JULIA_NUM_GC_THREADS).

!!! compat "Julia 1.10"
    L'argument de ligne de commande `--gcthreads` nécessite au moins Julia 1.10.


## [Threadpools](@id man-threadpools)

Lorsque les threads d'un programme sont occupés avec de nombreuses tâches à exécuter, les tâches peuvent subir des retards qui peuvent affecter négativement la réactivité et l'interactivité du programme. Pour y remédier, vous pouvez spécifier qu'une tâche est interactive lorsque vous [`Threads.@spawn`](@ref) cela :

```julia
using Base.Threads
@spawn :interactive f()
```

Les tâches interactives devraient éviter d'effectuer des opérations à haute latence, et si elles sont des tâches de longue durée, elles devraient céder fréquemment.

Julia peut être démarré avec un ou plusieurs threads réservés pour exécuter des tâches interactives :

```bash
$ julia --threads 3,1
```

La variable d'environnement [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) peut également être utilisée de manière similaire :

```bash
export JULIA_NUM_THREADS=3,1
```

Cela démarre Julia avec 3 threads dans le pool de threads `:default` et 1 thread dans le pool de threads `:interactive` :

```julia-repl
julia> using Base.Threads

julia> nthreadpools()
2

julia> threadpool() # the main thread is in the interactive thread pool
:interactive

julia> nthreads(:default)
3

julia> nthreads(:interactive)
1

julia> nthreads()
3
```

!!! note
    La version sans argument de `nthreads` renvoie le nombre de threads dans le pool par défaut.


!!! note
    Selon que Julia a été démarré avec des threads interactifs, le thread principal se trouve soit dans le pool de threads par défaut, soit dans le pool de threads interactifs.


Soit l'un ou l'autre des nombres peut être remplacé par le mot `auto`, ce qui amène Julia à choisir un défaut raisonnable.

## The `@threads` Macro

Créons un exemple simple en utilisant nos threads natifs. Créons un tableau de zéros :

```jldoctest
julia> a = zeros(10)
10-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
```

Faisons fonctionner ce tableau simultanément en utilisant 4 threads. Chaque thread écrira son ID de thread dans chaque emplacement.

Julia prend en charge les boucles parallèles en utilisant le [`Threads.@threads`](@ref) macro. Ce macro est placé devant une boucle `for` pour indiquer à Julia que la boucle est une région multi-threadée :

```julia-repl
julia> Threads.@threads for i = 1:10
           a[i] = Threads.threadid()
       end
```

L'espace d'itération est réparti entre les threads, après quoi chaque thread écrit son ID de thread dans ses emplacements assignés :

```julia-repl
julia> a
10-element Vector{Float64}:
 1.0
 1.0
 1.0
 2.0
 2.0
 2.0
 3.0
 3.0
 4.0
 4.0
```

Notez que [`Threads.@threads`](@ref) n'a pas de paramètre de réduction optionnel comme [`@distributed`](@ref).

### Using `@threads` without data-races

Le concept de course de données est élaboré dans ["Communication and data races between threads"](@ref man-communication-and-data-races). Pour l'instant, sachez simplement qu'une course de données peut entraîner des résultats incorrects et des erreurs dangereuses.

Disons que nous voulons rendre la fonction `sum_single` ci-dessous multithreadée.

```julia-repl
julia> function sum_single(a)
           s = 0
           for i in a
               s += i
           end
           s
       end
sum_single (generic function with 1 method)

julia> sum_single(1:1_000_000)
500000500000
```

Ajouter simplement `@threads` expose une condition de concurrence avec plusieurs threads lisant et écrivant `s` en même temps.

```julia-repl
julia> function sum_multi_bad(a)
           s = 0
           Threads.@threads for i in a
               s += i
           end
           s
       end
sum_multi_bad (generic function with 1 method)

julia> sum_multi_bad(1:1_000_000)
70140554652
```

Notez que le résultat n'est pas `500000500000` comme il devrait l'être, et changera très probablement à chaque évaluation.

Pour résoudre ce problème, des tampons spécifiques à la tâche peuvent être utilisés pour segmenter la somme en morceaux sans conflit. Ici, `sum_single` est réutilisé, avec son propre tampon interne `s`. Le vecteur d'entrée `a` est divisé en `nthreads()` morceaux pour un travail parallèle. Nous utilisons ensuite `Threads.@spawn` pour créer des tâches qui additionnent individuellement chaque morceau. Enfin, nous additionnons les résultats de chaque tâche en utilisant à nouveau `sum_single` :

```julia-repl
julia> function sum_multi_good(a)
           chunks = Iterators.partition(a, length(a) ÷ Threads.nthreads())
           tasks = map(chunks) do chunk
               Threads.@spawn sum_single(chunk)
           end
           chunk_sums = fetch.(tasks)
           return sum_single(chunk_sums)
       end
sum_multi_good (generic function with 1 method)

julia> sum_multi_good(1:1_000_000)
500000500000
```

!!! note
    Les tampons ne doivent pas être gérés en fonction de `threadid()` c'est-à-dire `buffers = zeros(Threads.nthreads())` car les tâches concurrentes peuvent céder, ce qui signifie que plusieurs tâches concurrentes peuvent utiliser le même tampon sur un thread donné, introduisant un risque de conditions de course. De plus, lorsque plus d'un thread est disponible, les tâches peuvent changer de thread aux points de cession, ce qui est connu sous le nom de [task migration](@ref man-task-migration).


Une autre option est l'utilisation d'opérations atomiques sur des variables partagées entre les tâches/threads, ce qui peut être plus performant en fonction des caractéristiques des opérations.

## [Communication and data-races between threads](@id man-communication-and-data-races)

Bien que les threads de Julia puissent communiquer par le biais de la mémoire partagée, il est notoirement difficile d'écrire un code multi-threadé correct et sans conditions de concurrence. Les [`Channel`](@ref) de Julia sont sûrs pour les threads et peuvent être utilisés pour communiquer en toute sécurité. Il y a aussi des sections ci-dessous qui expliquent comment utiliser [locks](@ref man-using-locks) et [atomics](@ref man-atomic-operations) pour éviter les conditions de concurrence.

### Data-race freedom

Vous êtes entièrement responsable de garantir que votre programme est exempt de conditions de concurrence, et rien de ce qui est promis ici ne peut être supposé si vous ne respectez pas cette exigence. Les résultats observés peuvent être très contre-intuitifs.

Si des courses de données sont introduites, Julia n'est pas sûre en mémoire. **Soyez très prudent lors de la lecture de *n'importe* quelle donnée si un autre thread pourrait y écrire, car cela pourrait entraîner des fautes de segmentation ou pire**. Voici quelques façons dangereuses d'accéder à des variables globales depuis différents threads :

```julia
Thread 1:
global b = false
global a = rand()
global b = true

Thread 2:
while !b; end
bad_read1(a) # it is NOT safe to access `a` here!

Thread 3:
while !@isdefined(a); end
bad_read2(a) # it is NOT safe to access `a` here
```

### [Using locks to avoid data-races](@id man-using-locks)

Un outil important pour éviter les courses de données, et ainsi écrire du code sûr pour les threads, est le concept de "verrou". Un verrou peut être verrouillé et déverrouillé. Si un thread a verrouillé un verrou, et ne l'a pas déverrouillé, on dit qu'il "détient" le verrou. S'il n'y a qu'un seul verrou, et que nous écrivons du code qui nécessite de détenir le verrou pour accéder à certaines données, nous pouvons garantir que plusieurs threads n'accéderont jamais aux mêmes données simultanément. Notez que le lien entre un verrou et une variable est établi par le programmeur, et non par le programme.

Par exemple, nous pouvons créer un verrou `my_lock`, et le verrouiller pendant que nous modifions une variable `my_variable`. Cela se fait de la manière la plus simple avec le macro `@lock` :

```julia-repl
julia> my_lock = ReentrantLock();

julia> my_variable = [1, 2, 3];

julia> @lock my_lock my_variable[1] = 100
100
```

En utilisant un modèle similaire avec le même verrou et la même variable, mais sur un autre thread, les opérations sont exemptes de conditions de concurrence.

Nous aurions pu effectuer l'opération ci-dessus avec la version fonctionnelle de `lock`, de deux manières suivantes :

```julia-repl
julia> lock(my_lock) do
           my_variable[1] = 100
       end
100

julia> begin
           lock(my_lock)
           try
               my_variable[1] = 100
           finally
               unlock(my_lock)
           end
       end
100
```

Les trois options sont équivalentes. Notez que la version finale nécessite un bloc `try` explicite pour s'assurer que le verrou est toujours déverrouillé, tandis que les deux premières versions le font en interne. On doit toujours utiliser le modèle de verrouillage ci-dessus lors de la modification de données (comme l'attribution à une variable globale ou de fermeture) accessibles par d'autres threads. Ne pas le faire pourrait avoir des conséquences imprévues et graves.

### [Atomic Operations](@id man-atomic-operations)

Julia prend en charge l'accès et la modification des valeurs *atomiquement*, c'est-à-dire de manière sécurisée pour les threads afin d'éviter [race conditions](https://en.wikipedia.org/wiki/Race_condition). Une valeur (qui doit être d'un type primitif) peut être encapsulée comme [`Threads.Atomic`](@ref) pour indiquer qu'elle doit être accédée de cette manière. Ici, nous pouvons voir un exemple :

```julia-repl
julia> i = Threads.Atomic{Int}(0);

julia> ids = zeros(4);

julia> old_is = zeros(4);

julia> Threads.@threads for id in 1:4
           old_is[id] = Threads.atomic_add!(i, id)
           ids[id] = id
       end

julia> old_is
4-element Vector{Float64}:
 0.0
 1.0
 7.0
 3.0

julia> i[]
 10

julia> ids
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
```

Si nous avions essayé de faire l'addition sans le tag atomique, nous aurions pu obtenir la mauvaise réponse en raison d'une condition de concurrence. Un exemple de ce qui se passerait si nous n'évitons pas la course :

```julia-repl
julia> using Base.Threads

julia> Threads.nthreads()
4

julia> acc = Ref(0)
Base.RefValue{Int64}(0)

julia> @threads for i in 1:1000
          acc[] += 1
       end

julia> acc[]
926

julia> acc = Atomic{Int64}(0)
Atomic{Int64}(0)

julia> @threads for i in 1:1000
          atomic_add!(acc, 1)
       end

julia> acc[]
1000
```

#### [Per-field atomics](@id man-atomics)

Nous pouvons également utiliser des atomiques à un niveau plus granulaire en utilisant les macros [`@atomic`](@ref Base.@atomic), [`@atomicswap`](@ref Base.@atomicswap), [`@atomicreplace`](@ref Base.@atomicreplace) et [`@atomiconce`](@ref Base.@atomiconce).

Les détails spécifiques du modèle de mémoire et d'autres détails de la conception sont écrits dans le [Julia Atomics Manifesto](https://gist.github.com/vtjnash/11b0031f2e2a66c9c24d33e810b34ec0), qui sera publié formellement plus tard.

Tout champ dans une déclaration de struct peut être décoré avec `@atomic`, et toute écriture doit également être marquée avec `@atomic` et doit utiliser l'un des ordonnancements atomiques définis (`:monotonic`, `:acquire`, `:release`, `:acquire_release` ou `:sequentially_consistent`). Toute lecture d'un champ atomique peut également être annotée avec une contrainte d'ordonnancement atomique, ou sera effectuée avec un ordonnancement monotone (relaxé) si non spécifié.

!!! compat "Julia 1.7"
    Les atomes par champ nécessitent au moins Julia 1.7.


## Side effects and mutable function arguments

Lorsque vous utilisez le multi-threading, vous devez faire attention lorsque vous utilisez des fonctions qui ne sont pas [pure](https://en.wikipedia.org/wiki/Pure_function), car nous pourrions obtenir une réponse incorrecte. Par exemple, les fonctions qui ont un [name ending with `!`](@ref bang-convention) modifient par convention leurs arguments et ne sont donc pas pures.

## @threadcall

Les bibliothèques externes, telles que celles appelées via [`ccall`](@ref), posent un problème pour le mécanisme d'E/S basé sur des tâches de Julia. Si une bibliothèque C effectue une opération bloquante, cela empêche le planificateur de Julia d'exécuter d'autres tâches jusqu'à ce que l'appel retourne. (Les exceptions sont les appels dans du code C personnalisé qui rappellent Julia, ce qui peut alors céder, ou le code C qui appelle `jl_yield()`, l'équivalent C de [`yield`](@ref).)

Le macro [`@threadcall`](@ref) fournit un moyen d'éviter de bloquer l'exécution dans un tel scénario. Il planifie une fonction C pour exécution dans un thread séparé. Un pool de threads de taille par défaut de 4 est utilisé pour cela. La taille du pool de threads est contrôlée via la variable d'environnement `UV_THREADPOOL_SIZE`. En attendant un thread libre, et pendant l'exécution de la fonction une fois qu'un thread est disponible, la tâche demandée (sur la boucle d'événements principale de Julia) cède la place à d'autres tâches. Notez que `@threadcall` ne retourne pas tant que l'exécution n'est pas terminée. Du point de vue de l'utilisateur, c'est donc un appel bloquant comme d'autres API de Julia.

Il est très important que la fonction appelée ne rappelle pas Julia, car cela entraînera un segfault.

`@threadcall` peut être supprimé ou modifié dans les futures versions de Julia.

## Caveats

À ce stade, la plupart des opérations dans le runtime Julia et les bibliothèques standard peuvent être utilisées de manière sécurisée pour les threads, si le code utilisateur est exempt de conditions de concurrence. Cependant, dans certains domaines, des travaux sont en cours pour stabiliser le support des threads. La programmation multi-threadée présente de nombreuses difficultés inhérentes, et si un programme utilisant des threads présente un comportement inhabituel ou indésirable (par exemple, des plantages ou des résultats mystérieux), les interactions entre threads doivent généralement être suspectées en premier.

Il y a quelques limitations et avertissements spécifiques à prendre en compte lors de l'utilisation des threads dans Julia :

  * Les types de collections de base nécessitent un verrouillage manuel s'ils sont utilisés simultanément par plusieurs threads, où au moins un thread modifie la collection (des exemples courants incluent `push!` sur des tableaux, ou l'insertion d'éléments dans un `Dict`).
  * Le calendrier utilisé par [`@spawn`](@ref Threads.@spawn) est non déterministe et ne doit pas être fiable.
  * Les tâches liées au calcul, qui n'allouent pas de mémoire, peuvent empêcher la collecte des ordures de s'exécuter dans d'autres threads qui allouent de la mémoire. Dans ces cas, il peut être nécessaire d'insérer un appel manuel à `GC.safepoint()` pour permettre à la collecte des ordures de s'exécuter. Cette limitation sera supprimée à l'avenir.
  * Évitez d'exécuter des opérations de haut niveau, par exemple `include`, ou `eval` de définitions de type, de méthode et de module en parallèle.
  * Soyez conscient que les finalisateurs enregistrés par une bibliothèque peuvent être rompus si les threads sont activés. Cela peut nécessiter un certain travail de transition à travers l'écosystème avant que le multithreading puisse être largement adopté en toute confiance. Voir la section sur [the safe use of finalizers](@ref man-finalizers) pour plus de détails.

## [Task Migration](@id man-task-migration)

Après qu'une tâche commence à s'exécuter sur un certain fil, elle peut passer à un fil différent si la tâche cède.

De telles tâches ont peut-être été commencées avec [`@spawn`](@ref Threads.@spawn) ou [`@threads`](@ref Threads.@threads), bien que l'option de planification `:static` pour `@threads` fige l'identifiant du thread.

Cela signifie que dans la plupart des cas, [`threadid()`](@ref Threads.threadid) ne doit pas être traité comme une constante dans une tâche, et ne doit donc pas être utilisé pour indexer un vecteur de tampons ou d'objets à état.

!!! compat "Julia 1.7"
    La migration des tâches a été introduite dans Julia 1.7. Avant cela, les tâches restaient toujours sur le même fil d'exécution sur lequel elles avaient été lancées.


## [Safe use of Finalizers](@id man-finalizers)

Parce que les finaliseurs peuvent interrompre n'importe quel code, ils doivent être très prudents dans la façon dont ils interagissent avec tout état global. Malheureusement, la principale raison pour laquelle les finaliseurs sont utilisés est de mettre à jour l'état global (une fonction pure est généralement plutôt inutile en tant que finaliseur). Cela nous conduit à une sorte de dilemme. Il existe quelques approches pour traiter ce problème :

1. Lorsque le code est à un seul fil, il peut appeler la fonction C interne `jl_gc_enable_finalizers` pour empêcher la planification des finaliseurs à l'intérieur d'une région critique. En interne, cela est utilisé dans certaines fonctions (comme nos verrous C) pour éviter la récursion lors de certaines opérations (chargement de paquets incrémental, génération de code, etc.). La combinaison d'un verrou et de ce drapeau peut être utilisée pour rendre les finaliseurs sûrs.
2. Une deuxième stratégie, utilisée par Base à plusieurs endroits, consiste à retarder explicitement un finaliseur jusqu'à ce qu'il puisse acquérir son verrou de manière non récursive. L'exemple suivant démontre comment cette stratégie pourrait être appliquée à `Distributed.finalize_ref` :

    ```julia
    function finalize_ref(r::AbstractRemoteRef)
        if r.where > 0 # Check if the finalizer is already run
            if islocked(client_refs) || !trylock(client_refs)
                # delay finalizer for later if we aren't free to acquire the lock
                finalizer(finalize_ref, r)
                return nothing
            end
            try # `lock` should always be followed by `try`
                if r.where > 0 # Must check again here
                    # Do actual cleanup here
                    r.where = 0
                end
            finally
                unlock(client_refs)
            end
        end
        nothing
    end
    ```
3. Une stratégie connexe est d'utiliser une file d'attente sans rendement. Nous n'avons actuellement pas de file d'attente sans verrou implémentée dans Base, mais `Base.IntrusiveLinkedListSynchronized{T}` est appropriée. Cela peut souvent être une bonne stratégie à utiliser pour le code avec des boucles d'événements. Par exemple, cette stratégie est employée par `Gtk.jl` pour gérer le comptage de références de durée de vie. Dans cette approche, nous ne faisons aucun travail explicite à l'intérieur du `finalizer`, et ajoutons plutôt cela à une file d'attente pour l'exécuter à un moment plus sûr. En fait, le planificateur de tâches de Julia utilise déjà cela, donc définir le finaliseur comme `x -> @spawn do_cleanup(x)` est un exemple de cette approche. Notez cependant que cela ne contrôle pas quel thread `do_cleanup` s'exécute, donc `do_cleanup` devrait toujours acquérir un verrou. Cela n'a pas besoin d'être vrai si vous implémentez votre propre file d'attente, car vous pouvez explicitement ne vider cette file d'attente que depuis votre thread.

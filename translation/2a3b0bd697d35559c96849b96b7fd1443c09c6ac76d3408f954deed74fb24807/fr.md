# [Asynchronous Programming](@id man-asynchronous)

Lorsque un programme doit interagir avec le monde extérieur, par exemple en communiquant avec une autre machine via Internet, les opérations dans le programme peuvent devoir se dérouler dans un ordre imprévisible. Supposons que votre programme doive télécharger un fichier. Nous aimerions initier l'opération de téléchargement, effectuer d'autres opérations pendant que nous attendons qu'elle se termine, puis reprendre le code qui a besoin du fichier téléchargé lorsqu'il est disponible. Ce type de scénario relève du domaine de la programmation asynchrone, parfois également appelée programmation concurrente (puisque, conceptuellement, plusieurs choses se produisent en même temps).

Pour aborder ces scénarios, Julia fournit des [`Task`](@ref) (également connus sous plusieurs autres noms, tels que coroutines symétriques, threads légers, multitâche coopératif ou continuations à usage unique). Lorsqu'un travail de calcul (en pratique, l'exécution d'une fonction particulière) est désigné comme un `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566`, il devient possible de l'interrompre en passant à un autre `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566`. Le `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` original peut ensuite être repris, moment auquel il reprendra exactement là où il s'était arrêté. Au début, cela peut sembler similaire à un appel de fonction. Cependant, il y a deux différences clés. Premièrement, le changement de tâches n'utilise aucun espace, donc un nombre quelconque de changements de tâches peut se produire sans consommer la pile d'appels. Deuxièmement, le changement entre les tâches peut se produire dans n'importe quel ordre, contrairement aux appels de fonction, où la fonction appelée doit terminer son exécution avant que le contrôle ne retourne à la fonction appelante.

## Basic `Task` operations

Vous pouvez considérer une `Task` comme un identifiant pour une unité de travail computationnel à réaliser. Elle a un cycle de vie de création-démarrage-exécution-terminaison. Les tâches sont créées en appelant le constructeur `Task` sur une fonction à 0 argument à exécuter, ou en utilisant la macro [`@task`](@ref) :

```julia-repl
julia> t = @task begin; sleep(5); println("done"); end
Task (runnable) @0x00007f13a40c0eb0
```

`@task x` est équivalent à `Task(()->x)`.

Cette tâche attendra cinq secondes, puis imprimera `fait`. Cependant, elle n'a pas encore commencé à s'exécuter. Nous pouvons l'exécuter quand nous sommes prêts en appelant [`schedule`](@ref) :

```julia-repl
julia> schedule(t);
```

Si vous essayez cela dans le REPL, vous verrez que `schedule` retourne immédiatement. Cela est dû au fait qu'il ajoute simplement `t` à une file d'attente interne de tâches à exécuter. Ensuite, le REPL affichera l'invite suivante et attendra plus d'entrées. Attendre une entrée au clavier offre une opportunité pour que d'autres tâches s'exécutent, donc à ce moment-là, `t` commencera. `t` appelle [`sleep`](@ref), qui définit un minuteur et arrête l'exécution. Si d'autres tâches ont été planifiées, elles pourraient s'exécuter alors. Après cinq secondes, le minuteur se déclenche et redémarre `t`, et vous verrez `done` affiché. `t` est alors terminé.

La fonction [`wait`](@ref) bloque la tâche appelante jusqu'à ce qu'une autre tâche se termine. Donc, par exemple, si vous tapez

```julia-repl
julia> schedule(t); wait(t)
```

au lieu d'appeler uniquement `schedule`, vous verrez une pause de cinq secondes avant que le prochain invite d'entrée n'apparaisse. Cela est dû au fait que le REPL attend que `t` se termine avant de continuer.

Il est courant de vouloir créer une tâche et de la planifier immédiatement, donc la macro [`@async`](@ref) est fournie à cet effet –- `@async x` est équivalent à `schedule(@task x)`.

## Communicating with Channels

Dans certains problèmes, les différentes tâches requises ne sont pas naturellement liées par des appels de fonction ; il n'y a pas de "caller" ou de "callee" évident parmi les tâches à accomplir. Un exemple est le problème du producteur-consommateur, où une procédure complexe génère des valeurs et une autre procédure complexe les consomme. Le consommateur ne peut pas simplement appeler une fonction de producteur pour obtenir une valeur, car le producteur peut avoir d'autres valeurs à générer et peut donc ne pas être encore prêt à retourner. Avec des tâches, le producteur et le consommateur peuvent tous deux s'exécuter aussi longtemps qu'ils en ont besoin, passant des valeurs d'avant en arrière si nécessaire.

Julia fournit un mécanisme [`Channel`](@ref) pour résoudre ce problème. Un `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` est une file d'attente FIFO (premier entré, premier sorti) attendable qui peut avoir plusieurs tâches lisant et écrivant dedans.

Définissons une tâche de producteur, qui produit des valeurs via l'appel [`put!`](@ref). Pour consommer des valeurs, nous devons planifier le producteur pour qu'il s'exécute dans une nouvelle tâche. Un constructeur spécial [`Channel`](@ref) qui accepte une fonction à un argument comme argument peut être utilisé pour exécuter une tâche liée à un canal. Nous pouvons ensuite [`take!`](@ref) des valeurs de manière répétée à partir de l'objet canal :

```jldoctest producer
julia> function producer(c::Channel)
           put!(c, "start")
           for n=1:4
               put!(c, 2n)
           end
           put!(c, "stop")
       end;

julia> chnl = Channel(producer);

julia> take!(chnl)
"start"

julia> take!(chnl)
2

julia> take!(chnl)
4

julia> take!(chnl)
6

julia> take!(chnl)
8

julia> take!(chnl)
"stop"
```

Une façon de penser à ce comportement est que `producer` a pu retourner plusieurs fois. Entre les appels à [`put!`](@ref), l'exécution du producteur est suspendue et le consommateur a le contrôle.

Le [`Channel`](@ref) retourné peut être utilisé comme un objet itérable dans une boucle `for`, auquel cas la variable de boucle prend toutes les valeurs produites. La boucle est terminée lorsque le canal est fermé.

```jldoctest producer
julia> for x in Channel(producer)
           println(x)
       end
start
2
4
6
8
stop
```

Notez que nous n'avons pas eu besoin de fermer explicitement le canal dans le producteur. Cela est dû au fait que l'acte de lier un [`Channel`](@ref) à un [`Task`](@ref) associe la durée de vie ouverte d'un canal à celle de la tâche liée. L'objet canal est fermé automatiquement lorsque la tâche se termine. Plusieurs canaux peuvent être liés à une tâche, et vice versa.

Alors que le constructeur [`Task`](@ref) attend une fonction sans argument, la méthode [`Channel`](@ref) qui crée un canal lié à une tâche attend une fonction qui accepte un seul argument de type `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`. Un modèle courant est que le producteur soit paramétré, auquel cas une application partielle de fonction est nécessaire pour créer une fonction avec 0 ou 1 argument [anonymous function](@ref man-anonymous-functions).

Pour [`Task`](@ref) objets, cela peut être fait soit directement, soit en utilisant une macro de commodité :

```julia
function mytask(myarg)
    ...
end

taskHdl = Task(() -> mytask(7))
# or, equivalently
taskHdl = @task mytask(7)
```

Pour orchestrer des modèles de distribution de travail plus avancés, [`bind`](@ref) et [`schedule`](@ref) peuvent être utilisés en conjonction avec [`Task`](@ref) et [`Channel`](@ref) pour lier explicitement un ensemble de canaux avec un ensemble de tâches de producteur/consommateur.

### More on Channels

Un canal peut être visualisé comme un tuyau, c'est-à-dire qu'il a une extrémité d'écriture et une extrémité de lecture :

  * Plusieurs écrivains dans différentes tâches peuvent écrire dans le même canal simultanément via des appels [`put!`](@ref).
  * Plusieurs lecteurs dans différentes tâches peuvent lire des données de manière concurrente via des appels [`take!`](@ref).
  * En tant qu'exemple :

    ```julia
    # Given Channels c1 and c2,
    c1 = Channel(32)
    c2 = Channel(32)

    # and a function `foo` which reads items from c1, processes the item read
    # and writes a result to c2,
    function foo()
        while true
            data = take!(c1)
            [...]               # process data
            put!(c2, result)    # write out result
        end
    end

    # we can schedule `n` instances of `foo` to be active concurrently.
    for _ in 1:n
        errormonitor(@async foo())
    end
    ```
  * Les canaux sont créés via le constructeur `Channel{T}(sz)`. Le canal ne contiendra que des objets de type `T`. Si le type n'est pas spécifié, le canal peut contenir des objets de n'importe quel type. `sz` fait référence au nombre maximum d'éléments qui peuvent être contenus dans le canal à tout moment. Par exemple, `Channel(32)` crée un canal qui peut contenir un maximum de 32 objets de n'importe quel type. Un `Channel{MyType}(64)` peut contenir jusqu'à 64 objets de `MyType` à tout moment.
  * Si un [`Channel`](@ref) est vide, les lecteurs (sur un [`take!`](@ref) appel) bloqueront jusqu'à ce que des données soient disponibles.
  * Si un [`Channel`](@ref) est plein, les écrivains (sur un [`put!`](@ref) appel) seront bloqués jusqu'à ce qu'un espace devienne disponible.
  * [`isready`](@ref) teste la présence de tout objet dans le canal, tandis que [`wait`](@ref) attend qu'un objet devienne disponible.
  * Un [`Channel`](@ref) est dans un état ouvert initialement. Cela signifie qu'il peut être lu et écrit librement via [`take!`](@ref) et [`put!`](@ref) appels. [`close`](@ref) ferme un `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`. Sur un `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` fermé, `4d61726b646f776e2e436f64652822222c2022707574212229_40726566` échouera. Par exemple :

    ```julia-repl
    julia> c = Channel(2);

    julia> put!(c, 1) # `put!` on an open channel succeeds
    1

    julia> close(c);

    julia> put!(c, 2) # `put!` on a closed channel throws an exception.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```
  * [`take!`](@ref) et [`fetch`](@ref) (qui récupère mais ne supprime pas la valeur) sur un canal fermé renvoient avec succès toutes les valeurs existantes jusqu'à ce qu'il soit vidé. En continuant l'exemple ci-dessus :

    ```julia-repl
    julia> fetch(c) # Any number of `fetch` calls succeed.
    1

    julia> fetch(c)
    1

    julia> take!(c) # The first `take!` removes the value.
    1

    julia> take!(c) # No more data available on a closed channel.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```

Considérons un exemple simple utilisant des canaux pour la communication inter-tâches. Nous démarrons 4 tâches pour traiter des données à partir d'un seul canal `jobs`. Les travaux, identifiés par un id (`job_id`), sont écrits dans le canal. Chaque tâche dans cette simulation lit un `job_id`, attend un temps aléatoire et renvoie un tuple de `job_id` et du temps simulé au canal des résultats. Enfin, tous les `results` sont imprimés.

```julia-repl
julia> const jobs = Channel{Int}(32);

julia> const results = Channel{Tuple}(32);

julia> function do_work()
           for job_id in jobs
               exec_time = rand()
               sleep(exec_time)                # simulates elapsed time doing actual work
                                               # typically performed externally.
               put!(results, (job_id, exec_time))
           end
       end;

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for i in 1:4 # start 4 tasks to process requests in parallel
           errormonitor(@async do_work())
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds")
           global n = n - 1
       end
4 finished in 0.22 seconds
3 finished in 0.45 seconds
1 finished in 0.5 seconds
7 finished in 0.14 seconds
2 finished in 0.78 seconds
5 finished in 0.9 seconds
9 finished in 0.36 seconds
6 finished in 0.87 seconds
8 finished in 0.79 seconds
10 finished in 0.64 seconds
12 finished in 0.5 seconds
11 finished in 0.97 seconds
0.029772311
```

Au lieu de `errormonitor(t)`, une solution plus robuste pourrait être d'utiliser `bind(results, t)`, car cela permettra non seulement de consigner les échecs inattendus, mais aussi de forcer la fermeture des ressources associées et de propager l'exception partout.

## More task operations

Les opérations de tâche sont basées sur une primitive de bas niveau appelée [`yieldto`](@ref). `yieldto(task, value)` suspend la tâche actuelle, passe à la `task` spécifiée et fait en sorte que le dernier appel de `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` de cette tâche retourne la `value` spécifiée. Remarquez que `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` est la seule opération requise pour utiliser le flux de contrôle de style tâche ; au lieu d'appeler et de retourner, nous passons toujours à une tâche différente. C'est pourquoi cette fonctionnalité est également appelée "coroutines symétriques" ; chaque tâche est commutée vers et depuis en utilisant le même mécanisme.

[`yieldto`](@ref) est puissant, mais la plupart des utilisations des tâches ne l'invoquent pas directement. Considérez pourquoi cela pourrait être. Si vous passez à une autre tâche, vous voudrez probablement revenir à celle-ci à un moment donné, mais savoir quand revenir et savoir quelle tâche a la responsabilité de revenir peut nécessiter une coordination considérable. Par exemple, [`put!`](@ref) et [`take!`](@ref) sont des opérations bloquantes, qui, lorsqu'elles sont utilisées dans le contexte des canaux, maintiennent un état pour se souvenir de qui sont les consommateurs. Ne pas avoir besoin de suivre manuellement la tâche consommatrice est ce qui rend `4d61726b646f776e2e436f64652822222c2022707574212229_40726566` plus facile à utiliser que le `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` de bas niveau.

En plus de [`yieldto`](@ref), quelques autres fonctions de base sont nécessaires pour utiliser les tâches efficacement.

  * [`current_task`](@ref) obtient une référence à la tâche actuellement en cours d'exécution.
  * [`istaskdone`](@ref) interroge si une tâche a quitté.
  * [`istaskstarted`](@ref) interroge si une tâche a déjà été exécutée.
  * [`task_local_storage`](@ref) manipule un magasin de clés-valeurs spécifique à la tâche actuelle.

## Tasks and events

La plupart des changements de tâche se produisent en raison de l'attente d'événements tels que des requêtes d'E/S, et sont effectués par un planificateur inclus dans Julia Base. Le planificateur maintient une file d'attente de tâches exécutables et exécute une boucle d'événements qui redémarre les tâches en fonction d'événements externes tels que l'arrivée de messages.

The basic function for waiting for an event is [`wait`](@ref). Several objects implement [`wait`](@ref); for example, given a `Process` object, [`wait`](@ref) will wait for it to exit. [`wait`](@ref) is often implicit; for example, a [`wait`](@ref) can happen inside a call to [`read`](@ref) to wait for data to be available.

Dans tous ces cas, [`wait`](@ref) opère finalement sur un objet [`Condition`](@ref), qui est chargé de mettre en file d'attente et de redémarrer les tâches. Lorsqu'une tâche appelle `4d61726b646f776e2e436f64652822222c2022776169742229_40726566` sur un `4d61726b646f776e2e436f64652822222c2022436f6e646974696f6e2229_40726566`, la tâche est marquée comme non exécutable, ajoutée à la file d'attente de la condition, et passe au planificateur. Le planificateur choisira alors une autre tâche à exécuter, ou se bloquera en attendant des événements externes. Si tout se passe bien, finalement un gestionnaire d'événements appellera [`notify`](@ref) sur la condition, ce qui fait que les tâches attendant cette condition redeviennent exécutables.

Une tâche créée explicitement en appelant [`Task`](@ref) n'est initialement pas connue du planificateur. Cela vous permet de gérer les tâches manuellement en utilisant [`yieldto`](@ref) si vous le souhaitez. Cependant, lorsqu'une telle tâche attend un événement, elle est toujours redémarrée automatiquement lorsque l'événement se produit, comme vous pouvez l'attendre.

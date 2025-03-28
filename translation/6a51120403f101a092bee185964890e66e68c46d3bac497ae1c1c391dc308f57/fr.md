# Instrumenting Julia with DTrace, and bpftrace

DTrace et bpftrace sont des outils qui permettent une instrumentation légère des processus. Vous pouvez activer et désactiver l'instrumentation pendant que le processus est en cours d'exécution, et avec l'instrumentation désactivée, la surcharge est minimale.

!!! compat "Julia 1.8"
    Le support pour les probes a été ajouté dans Julia 1.8


!!! note
    Cette documentation a été rédigée d'un point de vue Linux, la plupart de cela devrait s'appliquer à Mac OS/Darwin et FreeBSD.


## Enabling support

Sur Linux, installez le paquet `systemtap` qui contient une version de `dtrace` et créez un fichier `Make.user` contenant

```
WITH_DTRACE=1
```

pour activer les sondes USDT.

### Verifying

```
> readelf -n usr/lib/libjulia-internal.so.1

Displaying notes found in: .note.gnu.build-id
  Owner                Data size  Description
  GNU                  0x00000014 NT_GNU_BUILD_ID (unique build ID bitstring)
    Build ID: 57161002f35548772a87418d2385c284ceb3ead8

Displaying notes found in: .note.stapsdt
  Owner                Data size  Description
  stapsdt              0x00000029 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__begin
    Location: 0x000000000013213e, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cac
    Arguments:
  stapsdt              0x00000032 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__stop_the_world
    Location: 0x0000000000132144, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cae
    Arguments:
  stapsdt              0x00000027 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__end
    Location: 0x000000000013214a, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb0
    Arguments:
  stapsdt              0x0000002d NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__finalizer
    Location: 0x0000000000132150, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb2
    Arguments:
```

## Adding probes in libjulia

Les probes sont déclarées au format dtraces dans le fichier `src/uprobes.d`. Le fichier d'en-tête généré est inclus dans `src/julia_internal.h` et si vous ajoutez des probes, vous devez fournir une implémentation noop là-bas.

L'en-tête contiendra un sémaphore `*_ENABLED` et l'appel réel à la sonde. Si les arguments de la sonde sont coûteux à calculer, vous devez d'abord vérifier si la sonde est activée, puis calculer les arguments et appeler la sonde.

```c
  if (JL_PROBE_{PROBE}_ENABLED())
    auto expensive_arg = ...;
    JL_PROBE_{PROBE}(expensive_arg);
```

Si votre sonde n'a pas d'arguments, il est préférable de ne pas inclure la vérification du sémaphore. Avec les sondes USDT activées, le coût d'un sémaphore est une charge mémoire, indépendamment du fait que la sonde soit activée ou non.

```c
#define JL_PROBE_GC_BEGIN_ENABLED() __builtin_expect (julia_gc__begin_semaphore, 0)
__extension__ extern unsigned short julia_gc__begin_semaphore __attribute__ ((unused)) __attribute__ ((section (".probes")));
```

Alors que la sonde elle-même est un traîneau noop qui sera patché à un trampoline vers le gestionnaire de sonde.

## Available probes

### GC probes

1. `julia:gc__begin`: Le GC commence à s'exécuter sur un thread et déclenche un arrêt du monde.
2. `julia:gc__stop_the_world`: Tous les threads ont atteint un point de sécurité et le GC s'exécute.
3. `julia:gc__mark__begin`: Début de la phase de marquage
4. `julia:gc__mark_end(scanned_bytes, perm_scanned)`: La phase de marquage est terminée
5. `julia:gc__sweep_begin(full)`: Début du balayage
6. `julia:gc__sweep_end`: Phase de balayage terminée
7. `julia:gc__end`: Le GC est terminé, les autres threads continuent de travailler
8. `julia:gc__finalizer`: Le thread GC initial a terminé l'exécution des finaliseurs

### Task runtime probes

1. `julia:rt__run__task(task)`: Changement de tâche `task` sur le thread actuel.
2. `julia:rt__pause__task(task)`: Changement de la tâche `task` sur le thread actuel.
3. `julia:rt__new__task(parent, child)`: La tâche `parent` a créé la tâche `child` sur le thread actuel.
4. `julia:rt__start__task(task)`: La tâche `task` a été démarrée pour la première fois avec une nouvelle pile.
5. `julia:rt__finish__task(tâche)`: La tâche `tâche` est terminée et ne s'exécutera plus.
6. `julia:rt__start__process__events(task)`: La tâche `task` a commencé à traiter les événements libuv.
7. `julia:rt__finish__process__events(task)`: La tâche `task` a terminé le traitement des événements libuv.

### Task queue probes

1. `julia:rt__taskq__insert(ptls, task)`: Le thread `ptls` a tenté d'insérer `task` dans une multiq PARTR.
2. `julia:rt__taskq__get(ptls, task)`: Le fil `ptls` a extrait `task` d'une multiq PARTR.

### Thread sleep/wake probes

1. `julia:rt__sleep__check__wake(ptls, old_state)`: Le thread (PTLS `ptls`) se réveille, précédemment dans l'état `old_state`.
2. `julia:rt__sleep__check__wakeup(ptls)`: Le thread (PTLS `ptls`) s'est réveillé tout seul.
3. `julia:rt__sleep__check__sleep(ptls)`: Le thread (PTLS `ptls`) tente de dormir.
4. `julia:rt__sleep__check__taskq__wake(ptls)`: Le thread (PTLS `ptls`) ne parvient pas à dormir en raison des tâches dans la file d'attente PARTR multiq.
5. `julia:rt__sleep__check__task__wake(ptls)`: Le thread (PTLS `ptls`) ne parvient pas à dormir en raison des tâches dans la file d'attente de travail de Base.
6. `julia:rt__sleep__check__uv__wake(ptls)`: Le thread (PTLS `ptls`) échoue à dormir en raison du réveil de libuv.

## Probe usage examples

### GC stop-the-world latency

Un exemple de script `bpftrace` est donné dans `contrib/gc_stop_the_world_latency.bt` et il crée un histogramme de la latence pour que tous les threads atteignent un safepoint.

Exécuter ce code Julia, avec `julia -t 2`

```
using Base.Threads

fib(x) = x <= 1 ? 1 : fib(x-1) + fib(x-2)

beaver = @spawn begin
    while true
        fib(30)
        # A manual safepoint is necessary since otherwise this loop
        # may never yield to GC.
        GC.safepoint()
    end
end

allocator = @spawn begin
    while true
        zeros(1024)
    end
end

wait(allocator)
```

et dans un deuxième terminal

```
> sudo contrib/bpftrace/gc_stop_the_world_latency.bt
Attaching 4 probes...
Tracing Julia GC Stop-The-World Latency... Hit Ctrl-C to end.
^C


@usecs[1743412]:
[4, 8)               971 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@|
[8, 16)              837 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@        |
[16, 32)             129 |@@@@@@                                              |
[32, 64)              10 |                                                    |
[64, 128)              1 |                                                    |
```

Nous pouvons voir la distribution de latence de la phase d'arrêt du monde dans le processus Julia exécuté.

### Task spawn monitor

Il est parfois utile de savoir quand une tâche en génère d'autres. Cela est très facile à voir avec `rt__new__task`. Le premier argument de la sonde, `parent`, est la tâche existante qui crée une nouvelle tâche. Cela signifie que si vous connaissez l'adresse de la tâche que vous souhaitez surveiller, vous pouvez facilement regarder les tâches que cette tâche spécifique a générées. Voyons comment faire cela ; commençons d'abord une session Julia et obtenons le PID et l'adresse de la tâche du REPL :

```
> julia
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825

2> current_task()
Task (runnable) @0x00007f524d088010
```

Maintenant, nous pouvons démarrer `bpftrace` et le faire surveiller `rt__new__task` pour *seulement* ce parent :

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task /arg0==0x00007f524d088010/{ printf("Tâche : %x\n", arg0); }'`

(Notez que dans ce qui précède, `arg0` est le premier argument, `parent`).

Et si nous lançons une seule tâche :

`@async 1+1`

nous voyons cette tâche être créée :

`Tâche : 4d088010`

Cependant, si nous générons une multitude de tâches à partir de cette tâche nouvellement créée :

```julia
@async for i in 1:10
   @async 1+1
end
```

nous ne voyons toujours qu'une seule tâche de `bpftrace` :

`Tâche : 4d088010`

et c'est toujours la même tâche que nous surveillons ! Bien sûr, nous pouvons supprimer ce filtre pour voir *toutes* les tâches nouvellement créées tout aussi facilement :

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task { printf("Tâche : %x\n", arg0); }'`

```
Task: 4d088010
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
```

Nous pouvons voir notre tâche racine, et la tâche nouvellement créée comme le parent des dix tâches encore plus récentes.

### Thundering herd detection

Les temps d'exécution des tâches peuvent souvent souffrir du problème du "troupeau tonitruant" : lorsque du travail est ajouté à un temps d'exécution de tâche calme, tous les threads peuvent être réveillés de leur sommeil, même s'il n'y a pas assez de travail pour que chaque thread puisse traiter. Cela peut entraîner une latence supplémentaire et des cycles CPU pendant que tous les threads se réveillent (et retournent simultanément au sommeil, ne trouvant aucun travail à exécuter).

Nous pouvons voir ce problème illustré avec `bpftrace` assez facilement. Tout d'abord, dans un terminal, nous démarrons Julia avec plusieurs threads (6 dans cet exemple) et obtenons le PID de ce processus :

```
> julia -t 6
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825
```

Et dans un autre terminal, nous démarrons `bpftrace` pour surveiller notre processus, en sondant spécifiquement le crochet `rt__sleep__check__wake` :

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__sleep__check__wake { printf("Réveil du thread ! %x\n", arg0); }'`

Maintenant, nous créons et exécutons une seule tâche en Julia :

`Threads.@spawn 1+1`

Et dans `bpftrace`, nous voyons imprimé quelque chose comme :

```
Thread wake up! 3f926100
Thread wake up! 3ebd5140
Thread wake up! 3f876130
Thread wake up! 3e2711a0
Thread wake up! 3e312190
```

Même si nous n'avons créé qu'une seule tâche (qui ne pouvait être traitée que par un seul thread à la fois), nous avons réveillé tous nos autres threads ! À l'avenir, un runtime de tâche plus intelligent pourrait ne réveiller qu'un seul thread (ou aucun ; le thread qui a créé la tâche pourrait exécuter cette tâche !), et nous devrions voir ce comportement disparaître.

### Task Monitor with BPFnative.jl

BPFnative.jl est capable de se connecter aux points de sonde USDT tout comme `bpftrace`. Une démonstration est disponible pour surveiller le temps d'exécution des tâches, le GC et les transitions de sommeil/réveil des threads [here](https://github.com/jpsamaroo/BPFnative.jl/blob/master/examples/task-runtime.jl).

## Notes on using `bpftrace`

Un exemple de sonde au format bpftrace ressemble à :

```
usdt:usr/lib/libjulia-internal.so:julia:gc__begin
{
  @start[pid] = nsecs;
}
```

La déclaration de la sonde prend le type `usdt`, puis soit le chemin vers la bibliothèque, soit le PID, le nom du fournisseur `julia` et le nom de la sonde `gc__begin`. Notez que j'utilise un chemin relatif vers le `libjulia-internal.so`, mais cela pourrait devoir être un chemin absolu sur un système de production.

## Useful references:

  * [Julia Evans blog on Linux tracing systems](https://jvns.ca/blog/2017/07/05/linux-tracing-systems)
  * [LWN article on USDT and BPF](https://lwn.net/Articles/753601/)
  * [GDB support for probes](https://sourceware.org/gdb/onlinedocs/gdb/Static-Probe-Points.html)
  * [Brendan Gregg – Linux Performance](https://www.brendangregg.com/linuxperf.html)

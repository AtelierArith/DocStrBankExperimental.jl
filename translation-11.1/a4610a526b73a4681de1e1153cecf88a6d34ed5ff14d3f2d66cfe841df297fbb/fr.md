```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Profile/docs/src/index.md"
```

# [Profiling](@id lib-profiling)

## CPU Profiling

Il existe deux approches principales pour le profilage CPU du code Julia :

## Via `@profile`

Là où le profilage est activé pour un appel donné via le macro `@profile`.

```julia-repl
julia> using Profile

julia> @profile foo()

julia> Profile.print()
Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
    ╎147  @Base/client.jl:506; _start()
        ╎ 147  @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...
```

## Triggered During Execution

Les tâches qui sont déjà en cours peuvent également être profilées pendant une période de temps fixe à tout moment déclenché par l'utilisateur.

Pour déclencher le profilage :

  * MacOS et FreeBSD (plateformes basées sur BSD) : Utilisez `ctrl-t` ou envoyez un signal `SIGINFO` au processus julia, c'est-à-dire `% kill -INFO $julia_pid`
  * Linux : Envoyez un signal `SIGUSR1` au processus julia c'est-à-dire `% kill -USR1 $julia_pid`
  * Windows : Pas actuellement pris en charge.

Tout d'abord, une seule trace de pile au moment où le signal a été lancé est affichée, puis un profil de 1 seconde est collecté, suivi du rapport de profil au prochain point de yield, qui peut être à l'achèvement de la tâche pour du code sans points de yield, par exemple des boucles serrées.

Optionnellement, définissez la variable d'environnement [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@ref JULIA_PROFILE_PEEK_HEAP_SNAPSHOT) à `1` pour également collecter automatiquement un [heap snapshot](@ref Heap-Snapshots).

```julia-repl
julia> foo()
##== the user sends a trigger while foo is running ==##
load: 2.53  cmd: julia 88903 running 6.16u 0.97s

======================================================================================
Information request received. A stacktrace will print followed by a 1.0 second profile
======================================================================================

signal (29): Information request: 29
__psynch_cvwait at /usr/lib/system/libsystem_kernel.dylib (unknown line)
_pthread_cond_wait at /usr/lib/system/libsystem_pthread.dylib (unknown line)
...

======================================================================
Profile collected. A report will print if the Profile module is loaded
======================================================================

Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
Thread 1 Task 0x000000011687c010 Total snapshots: 572. Utilization: 100%
   ╎147 @Base/client.jl:506; _start()
       ╎ 147 @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...

Thread 2 Task 0x0000000116960010 Total snapshots: 572. Utilization: 0%
   ╎572 @Base/task.jl:587; task_done_hook(t::Task)
      ╎ 572 @Base/task.jl:879; wait()
...
```

### Customization

La durée du profilage peut être ajustée via [`Profile.set_peek_duration`](@ref)

Le rapport de profil est divisé par fil et tâche. Passez une fonction sans argument à `Profile.peek_report[]` pour remplacer cela. c'est-à-dire `Profile.peek_report[] = () -> Profile.print()` pour supprimer tout regroupement. Cela pourrait également être remplacé par un consommateur de données de profil externe.

## Reference

```@docs
Profile.@profile
```

Les méthodes dans `Profile` ne sont pas exportées et doivent être appelées par exemple comme `Profile.print()`.

```@docs
Profile.clear
Profile.print
Profile.init
Profile.fetch
Profile.retrieve
Profile.callers
Profile.clear_malloc_data
Profile.get_peek_duration
Profile.set_peek_duration
```

## Memory profiling

```@docs
Profile.Allocs.@profile
```

Les méthodes dans `Profile.Allocs` ne sont pas exportées et doivent être appelées par exemple comme `Profile.Allocs.fetch()`.

```@docs
Profile.Allocs.clear
Profile.Allocs.print
Profile.Allocs.fetch
Profile.Allocs.start
Profile.Allocs.stop
```

## Heap Snapshots

```@docs
Profile.take_heap_snapshot
```

Les méthodes dans `Profile` ne sont pas exportées et doivent être appelées par exemple comme `Profile.take_heap_snapshot()`.

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot.heapsnapshot")
```

Trace et enregistre les objets Julia sur le tas. Cela n'enregistre que les objets connus du ramasse-miettes Julia. La mémoire allouée par des bibliothèques externes non gérées par le ramasse-miettes ne s'affichera pas dans l'instantané.

Pour éviter un OOM lors de l'enregistrement du snapshot, nous avons ajouté une option de streaming pour diffuser le snapshot de tas dans quatre fichiers,

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot"; streaming=true)
```

où "snapshot" est le chemin d'accès en tant que préfixe pour les fichiers générés.

Une fois les fichiers de snapshot générés, ils peuvent être assemblés hors ligne avec la commande suivante :

```julia-repl
julia> using Profile

julia> Profile.HeapSnapshot.assemble_snapshot("snapshot", "snapshot.heapsnapshot")
```

Le fichier de snapshot de tas résultant peut être téléchargé dans les outils de développement Chrome pour être visualisé. Pour plus d'informations, voir le [chrome devtools docs](https://developer.chrome.com/docs/devtools/memory-problems/heap-snapshots/#view_snapshots). Une alternative pour analyser les snapshots de tas Chromium est avec l'extension VS Code `ms-vscode.vscode-js-profile-flame`.

Les instantanés de tas de Firefox sont d'un format différent, et Firefox ne peut actuellement *pas* être utilisé pour visualiser les instantanés de tas générés par Julia.

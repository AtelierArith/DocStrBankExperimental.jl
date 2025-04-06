```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Profile/docs/src/index.md"
```

# [Profiling](@id lib-profiling)

## CPU Profiling

Es gibt zwei Hauptansätze zur CPU-Profilierung von Julia-Code:

## Via `@profile`

Wo das Profiling für einen bestimmten Aufruf über das `@profile`-Makro aktiviert ist.

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

Aufgaben, die bereits ausgeführt werden, können auch für einen festen Zeitraum zu einem beliebigen benutzergesteuerten Zeitpunkt profiliert werden.

Um das Profiling auszulösen:

  * MacOS & FreeBSD (BSD-basierte Plattformen): Verwenden Sie `ctrl-t` oder senden Sie ein `SIGINFO`-Signal an den Julia-Prozess, d.h. `% kill -INFO $julia_pid`
  * Linux: Senden Sie ein `SIGUSR1`-Signal an den Julia-Prozess, d.h. `% kill -USR1 $julia_pid`
  * Windows: Derzeit nicht unterstützt.

Zuerst wird ein einzelner Stack-Trace zum Zeitpunkt des Signals angezeigt, dann wird ein 1-Sekunden-Profil gesammelt, gefolgt von dem Profilbericht am nächsten Ertragspunkt, der möglicherweise am Ende der Aufgabe für Code ohne Ertragspunkte, z.B. enge Schleifen, liegt.

Optional setzen Sie die Umgebungsvariable [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@ref JULIA_PROFILE_PEEK_HEAP_SNAPSHOT) auf `1`, um auch automatisch einen [heap snapshot](@ref Heap-Snapshots) zu sammeln.

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

Die Dauer des Profilings kann über [`Profile.set_peek_duration`](@ref) angepasst werden.

Der Profilbericht ist nach Thread und Aufgabe unterteilt. Übergeben Sie eine Funktion ohne Argumente an `Profile.peek_report[]`, um dies zu überschreiben. z.B. `Profile.peek_report[] = () -> Profile.print()`, um jegliche Gruppierung zu entfernen. Dies könnte auch von einem externen Profil-Datenverbraucher überschrieben werden.

## Reference

```@docs
Profile.@profile
```

Die Methoden in `Profile` sind nicht exportiert und müssen z.B. als `Profile.print()` aufgerufen werden.

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

Die Methoden in `Profile.Allocs` sind nicht exportiert und müssen z.B. als `Profile.Allocs.fetch()` aufgerufen werden.

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

Die Methoden in `Profile` sind nicht exportiert und müssen z.B. als `Profile.take_heap_snapshot()` aufgerufen werden.

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot.heapsnapshot")
```

Verfolgt und zeichnet Julia-Objekte im Heap auf. Dies erfasst nur Objekte, die dem Julia-Garbage-Collector bekannt sind. Speicher, der von externen Bibliotheken zugewiesen wird, die nicht vom Garbage-Collector verwaltet werden, wird im Snapshot nicht angezeigt.

Um OOM zu vermeiden, während der Snapshot aufgenommen wird, haben wir eine Streaming-Option hinzugefügt, um den Heap-Snapshot in vier Dateien zu streamen,

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot"; streaming=true)
```

wo "snapshot" der Dateipfad als Präfix für die generierten Dateien ist.

Sobald die Snapshot-Dateien erstellt sind, können sie offline mit dem folgenden Befehl zusammengefügt werden:

```julia-repl
julia> using Profile

julia> Profile.HeapSnapshot.assemble_snapshot("snapshot", "snapshot.heapsnapshot")
```

Die resultierende Heap-Snapshot-Datei kann in Chrome DevTools hochgeladen werden, um sie anzuzeigen. Weitere Informationen finden Sie unter [chrome devtools docs](https://developer.chrome.com/docs/devtools/memory-problems/heap-snapshots/#view_snapshots). Eine Alternative zur Analyse von Chromium-Heap-Snapshots ist die VS Code-Erweiterung `ms-vscode.vscode-js-profile-flame`.

Die Firefox-Heap-Snapshots haben ein anderes Format, und Firefox kann derzeit *nicht* zum Anzeigen der von Julia generierten Heap-Snapshots verwendet werden.

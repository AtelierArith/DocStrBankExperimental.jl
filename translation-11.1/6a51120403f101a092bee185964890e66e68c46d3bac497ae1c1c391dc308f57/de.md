# Instrumenting Julia with DTrace, and bpftrace

DTrace und bpftrace sind Werkzeuge, die eine leichte Instrumentierung von Prozessen ermöglichen. Sie können die Instrumentierung ein- und ausschalten, während der Prozess läuft, und mit ausgeschalteter Instrumentierung ist der Overhead minimal.

!!! compat "Julia 1.8"
    Die Unterstützung für Proben wurde in Julia 1.8 hinzugefügt.


!!! note
    Diese Dokumentation wurde aus einer Linux-Perspektive verfasst, die meisten dieser Informationen sollten auch auf Mac OS/Darwin und FreeBSD zutreffen.


## Enabling support

Auf Linux installieren Sie das Paket `systemtap`, das eine Version von `dtrace` enthält, und erstellen Sie eine Datei `Make.user`, die Folgendes enthält:

```
WITH_DTRACE=1
```

USDT-Sonden aktivieren.

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

Proben werden im dtraces-Format in der Datei `src/uprobes.d` deklariert. Die generierte Header-Datei wird in `src/julia_internal.h` eingebunden, und wenn Sie Proben hinzufügen, sollten Sie dort eine noop-Implementierung bereitstellen.

Der Header enthält ein Semaphore `*_ENABLED` und den tatsächlichen Aufruf der Probe. Wenn die Argumente der Probe teuer zu berechnen sind, sollten Sie zuerst überprüfen, ob die Probe aktiviert ist, und dann die Argumente berechnen und die Probe aufrufen.

```c
  if (JL_PROBE_{PROBE}_ENABLED())
    auto expensive_arg = ...;
    JL_PROBE_{PROBE}(expensive_arg);
```

Wenn Ihr Probe keine Argumente hat, wird empfohlen, die Semaphore-Prüfung nicht einzuschließen. Mit aktivierten USDT-Proben ist die Kosten einer Semaphore ein Speicherzugriff, unabhängig davon, ob die Probe aktiviert ist oder nicht.

```c
#define JL_PROBE_GC_BEGIN_ENABLED() __builtin_expect (julia_gc__begin_semaphore, 0)
__extension__ extern unsigned short julia_gc__begin_semaphore __attribute__ ((unused)) __attribute__ ((section (".probes")));
```

Während die Sonde selbst ein Noop-Schlitten ist, der an ein Trampolin zum Sonde-Handler gepatcht wird.

## Available probes

### GC probes

1. `julia:gc__begin`: Die GC beginnt auf einem Thread zu laufen und löst eine Stop-the-World-Aktion aus.
2. `julia:gc__stop_the_world`: Alle Threads haben einen Safepoint erreicht und die GC läuft.
3. `julia:gc__mark__begin`: Beginn der Markierungsphase
4. `julia:gc__mark_end(scanned_bytes, perm_scanned)`: Markierungsphase beendet
5. `julia:gc__sweep_begin(full)`: Beginn der Sweep-Aktion
6. `julia:gc__sweep_end`: Sweep-Phase beendet
7. `julia:gc__end`: GC ist beendet, andere Threads setzen die Arbeit fort
8. `julia:gc__finalizer`: Der anfängliche GC-Thread hat das Ausführen der Finalisierer abgeschlossen.

### Task runtime probes

1. `julia:rt__run__task(task)`: Wechseln zu Aufgabe `task` im aktuellen Thread.
2. `julia:rt__pause__task(task)`: Wechseln von der Aufgabe `task` im aktuellen Thread.
3. `julia:rt__new__task(parent, child)`: Aufgabe `parent` hat die Aufgabe `child` im aktuellen Thread erstellt.
4. `julia:rt__start__task(task)`: Aufgabe `task` wurde zum ersten Mal mit einem neuen Stack gestartet.
5. `julia:rt__finish__task(task)`: Aufgabe `task` abgeschlossen und wird nicht mehr ausgeführt.
6. `julia:rt__start__process__events(task)`: Aufgabe `task` hat mit der Verarbeitung von libuv-Ereignissen begonnen.
7. `julia:rt__finish__process__events(task)`: Die Aufgabe `task` hat die Verarbeitung der libuv-Ereignisse abgeschlossen.

### Task queue probes

1. `julia:rt__taskq__insert(ptls, task)`: Der Thread `ptls` versuchte, `task` in eine PARTR-Multiq einzufügen.
2. `julia:rt__taskq__get(ptls, task)`: Der Thread `ptls` hat `task` aus einer PARTR-Multiq entfernt.

### Thread sleep/wake probes

1. `julia:rt__sleep__check__wake(ptls, old_state)`: Thread (PTLS `ptls`) wacht auf, zuvor im Zustand `old_state`.
2. `julia:rt__sleep__check__wakeup(ptls)`: Der Thread (PTLS `ptls`) hat sich selbst geweckt.
3. `julia:rt__sleep__check__sleep(ptls)`: Der Thread (PTLS `ptls`) versucht zu schlafen.
4. `julia:rt__sleep__check__taskq__wake(ptls)`: Der Thread (PTLS `ptls`) kann nicht schlafen, da Aufgaben in der PARTR-Multiq vorhanden sind.
5. `julia:rt__sleep__check__task__wake(ptls)`: Der Thread (PTLS `ptls`) kann aufgrund von Aufgaben in der Basis-Arbeitswarteschlange nicht schlafen.
6. `julia:rt__sleep__check__uv__wake(ptls)`: Der Thread (PTLS `ptls`) kann aufgrund der libuv-Aktivierung nicht schlafen.

## Probe usage examples

### GC stop-the-world latency

Ein Beispiel für ein `bpftrace`-Skript ist in `contrib/gc_stop_the_world_latency.bt` zu finden, und es erstellt ein Histogramm der Latenz für alle Threads, um einen Safepoint zu erreichen.

Führen Sie diesen Julia-Code aus, mit `julia -t 2`

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

und in einem zweiten Terminal

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

Wir können die Latenzverteilung der Stop-the-World-Phase im ausgeführten Julia-Prozess sehen.

### Task spawn monitor

Es ist manchmal nützlich zu wissen, wann eine Aufgabe andere Aufgaben erzeugt. Dies ist sehr einfach mit `rt__new__task` zu sehen. Das erste Argument des Probes, `parent`, ist die bestehende Aufgabe, die eine neue Aufgabe erstellt. Das bedeutet, dass Sie, wenn Sie die Adresse der Aufgabe kennen, die Sie überwachen möchten, einfach die Aufgaben ansehen können, die diese spezifische Aufgabe erzeugt hat. Lassen Sie uns sehen, wie man das macht; zuerst starten wir eine Julia-Sitzung und erhalten die PID und die Adresse der REPL-Aufgabe:

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

Jetzt können wir `bpftrace` starten und es `rt__new__task` nur für diesen Elternteil überwachen:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task /arg0==0x00007f524d088010/{ printf("Aufgabe: %x\n", arg0); }'`

(Hinweis: In dem obigen Beispiel ist `arg0` das erste Argument, `parent`.)

Und wenn wir eine einzelne Aufgabe erstellen:

`@async 1+1`

wir sehen, dass diese Aufgabe erstellt wird:

`Aufgabe: 4d088010`

Wenn wir jedoch eine Reihe von Aufgaben aus dieser neu gestarteten Aufgabe erzeugen:

```julia
@async for i in 1:10
   @async 1+1
end
```

wir sehen immer noch nur eine Aufgabe von `bpftrace`:

`Aufgabe: 4d088010`

und es ist immer noch die gleiche Aufgabe, die wir überwachen! Natürlich können wir diesen Filter entfernen, um *alle* neu erstellten Aufgaben ebenso einfach zu sehen:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task { printf("Aufgabe: %x\n", arg0); }'`

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

Wir können unsere Wurzelaufgabe sehen und die neu gestartete Aufgabe als die übergeordnete Aufgabe der zehn noch neueren Aufgaben.

### Thundering herd detection

Aufgabenlaufzeiten können oft unter dem "herdenartigen Donner"-Problem leiden: Wenn einige Arbeiten zu einer ruhigen Aufgabenlaufzeit hinzugefügt werden, können alle Threads aus ihrem Schlummer geweckt werden, selbst wenn nicht genügend Arbeit für jeden Thread vorhanden ist, um sie zu verarbeiten. Dies kann zusätzliche Latenz und CPU-Zyklen verursachen, während alle Threads aufwachen (und gleichzeitig wieder in den Schlaf zurückkehren, da sie keine Arbeit zum Ausführen finden).

Wir können dieses Problem ganz einfach mit `bpftrace` veranschaulichen. Zuerst starten wir in einem Terminal Julia mit mehreren Threads (6 in diesem Beispiel) und erhalten die PID dieses Prozesses:

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

Und in einem anderen Terminal starten wir die `bpftrace`-Überwachung unseres Prozesses, indem wir speziell den `rt__sleep__check__wake`-Hook abfragen:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__sleep__check__wake { printf("Thread aufgewacht! %x\n", arg0); }'`

Jetzt erstellen und führen wir eine einzelne Aufgabe in Julia aus:

`Threads.@spawn 1+1`

Und in `bpftrace` sehen wir etwas wie folgt ausgegeben:

```
Thread wake up! 3f926100
Thread wake up! 3ebd5140
Thread wake up! 3f876130
Thread wake up! 3e2711a0
Thread wake up! 3e312190
```

Auch wenn wir nur eine einzige Aufgabe erzeugt haben (die nur von einem Thread gleichzeitig verarbeitet werden konnte), haben wir alle unsere anderen Threads geweckt! In Zukunft könnte ein intelligenterer Aufgabenlaufzeit nur einen Thread (oder gar keinen; der erzeugende Thread könnte diese Aufgabe ausführen!) wecken, und wir sollten sehen, dass dieses Verhalten verschwindet.

### Task Monitor with BPFnative.jl

BPFnative.jl kann an USDT-Probe-Punkte angeschlossen werden, genau wie `bpftrace`. Es gibt eine Demo zur Überwachung der Laufzeit von Aufgaben, GC und der Übergänge von Threads zwischen Schlafen und Wachen unter [here](https://github.com/jpsamaroo/BPFnative.jl/blob/master/examples/task-runtime.jl).

## Notes on using `bpftrace`

Ein Beispiel für eine Probe im bpftrace-Format sieht so aus:

```
usdt:usr/lib/libjulia-internal.so:julia:gc__begin
{
  @start[pid] = nsecs;
}
```

Die Proben-Deklaration hat den Typ `usdt`, dann entweder den Pfad zur Bibliothek oder die PID, den Anbieternamen `julia` und den Probenamen `gc__begin`. Beachten Sie, dass ich einen relativen Pfad zur `libjulia-internal.so` verwende, dies jedoch auf einem Produktionssystem ein absoluter Pfad sein muss.

## Useful references:

  * [Julia Evans blog on Linux tracing systems](https://jvns.ca/blog/2017/07/05/linux-tracing-systems)
  * [LWN article on USDT and BPF](https://lwn.net/Articles/753601/)
  * [GDB support for probes](https://sourceware.org/gdb/onlinedocs/gdb/Static-Probe-Points.html)
  * [Brendan Gregg – Linux Performance](https://www.brendangregg.com/linuxperf.html)

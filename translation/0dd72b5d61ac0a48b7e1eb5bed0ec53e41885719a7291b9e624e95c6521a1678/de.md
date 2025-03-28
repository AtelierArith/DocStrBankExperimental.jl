```
Threads.foreach(f, channel::Channel;
                schedule::Threads.AbstractSchedule=Threads.FairSchedule(),
                ntasks=Threads.threadpoolsize())
```

Ähnlich wie `foreach(f, channel)`, aber die Iteration über `channel` und die Aufrufe von `f` werden auf `ntasks` Aufgaben verteilt, die von `Threads.@spawn` gestartet werden. Diese Funktion wartet darauf, dass alle intern gestarteten Aufgaben abgeschlossen sind, bevor sie zurückkehrt.

Wenn `schedule isa FairSchedule` ist, wird `Threads.foreach` versuchen, Aufgaben so zu starten, dass Julias Scheduler die Arbeitslast freier über die Threads ausbalancieren kann. Dieser Ansatz hat im Allgemeinen höhere Kosten pro Element, kann jedoch besser abschneiden als `StaticSchedule` in Verbindung mit anderen mehrthreadigen Arbeitslasten.

Wenn `schedule isa StaticSchedule` ist, wird `Threads.foreach` Aufgaben so starten, dass die Kosten pro Element niedriger sind als bei `FairSchedule`, aber weniger geeignet für die Lastenverteilung. Dieser Ansatz kann daher besser für feinkörnige, einheitliche Arbeitslasten geeignet sein, kann jedoch schlechter abschneiden als `FairSchedule` in Verbindung mit anderen mehrthreadigen Arbeitslasten.

# Beispiele

```julia-repl
julia> n = 20

julia> c = Channel{Int}(ch -> foreach(i -> put!(ch, i), 1:n), 1)

julia> d = Channel{Int}(n) do ch
           f = i -> put!(ch, i^2)
           Threads.foreach(f, c)
       end

julia> collect(d)
collect(d) = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
```

!!! compat "Julia 1.6"
    Diese Funktion erfordert Julia 1.6 oder höher.


```
Threads.@threads [schedule] for ... end
```

Ein Makro, um eine `for`-Schleife parallel auszuführen. Der Iterationsraum wird auf grobkörnige Aufgaben verteilt. Diese Richtlinie kann durch das Argument `schedule` angegeben werden. Die Ausführung der Schleife wartet auf die Auswertung aller Iterationen.

Siehe auch: [`@spawn`](@ref Threads.@spawn) und `pmap` in [`Distributed`](@ref man-distributed).

# Erweiterte Hilfe

## Semantik

Sofern nicht stärkere Garantien durch die Scheduling-Option angegeben sind, hat die von dem `@threads`-Makro ausgeführte Schleife die folgende Semantik.

Das `@threads`-Makro führt den Schleifeninhalt in einer nicht spezifizierten Reihenfolge und potenziell gleichzeitig aus. Es gibt keine genauen Zuordnungen der Aufgaben und der Arbeiter-Threads an. Die Zuordnungen können bei jeder Ausführung unterschiedlich sein. Der Code des Schleifeninhalts (einschließlich aller von ihm transitiv aufgerufenen Codes) darf keine Annahmen über die Verteilung der Iterationen auf Aufgaben oder den Arbeiter-Thread, in dem sie ausgeführt werden, treffen. Der Schleifeninhalt für jede Iteration muss in der Lage sein, unabhängig von anderen Iterationen Fortschritte zu machen und frei von Datenrennen zu sein. Daher können ungültige Synchronisationen zwischen Iterationen zu einem Deadlock führen, während unsynchronisierte Speicherzugriffe zu undefiniertem Verhalten führen können.

Zum Beispiel implizieren die obigen Bedingungen, dass:

  * Ein in einer Iteration *genommenes* Lock muss innerhalb derselben Iteration freigegeben werden.
  * Die Kommunikation zwischen Iterationen unter Verwendung blockierender Primitiven wie `Channel`s ist inkorrekt.
  * Nur an Orten schreiben, die nicht zwischen Iterationen geteilt werden (es sei denn, ein Lock oder eine atomare Operation wird verwendet).
  * Sofern nicht der `:static`-Zeitplan verwendet wird, kann der Wert von [`threadid()`](@ref Threads.threadid) selbst innerhalb einer einzigen Iteration variieren. Siehe [`Task Migration`](@ref man-task-migration).

## Scheduler

Ohne das Scheduler-Argument ist die genaue Planung nicht spezifiziert und variiert zwischen den Julia-Versionen. Derzeit wird `:dynamic` verwendet, wenn der Scheduler nicht angegeben ist.

!!! compat "Julia 1.5"
    Das `schedule`-Argument ist seit Julia 1.5 verfügbar.


### `:dynamic` (Standard)

Der `:dynamic`-Scheduler führt Iterationen dynamisch auf verfügbaren Arbeiter-Threads aus. Die aktuelle Implementierung geht davon aus, dass die Arbeitslast für jede Iteration gleichmäßig verteilt ist. Diese Annahme kann jedoch in Zukunft aufgehoben werden.

Diese Scheduling-Option ist lediglich ein Hinweis auf den zugrunde liegenden Ausführungsmechanismus. Es können jedoch einige Eigenschaften erwartet werden. Die Anzahl der von dem `:dynamic`-Scheduler verwendeten `Task`s ist durch ein kleines konstantes Vielfaches der Anzahl der verfügbaren Arbeiter-Threads ([`Threads.threadpoolsize()`](@ref)). Jede Aufgabe verarbeitet zusammenhängende Bereiche des Iterationsraums. Daher ist `@threads :dynamic for x in xs; f(x); end` typischerweise effizienter als `@sync for x in xs; @spawn f(x); end`, wenn `length(xs)` erheblich größer ist als die Anzahl der Arbeiter-Threads und die Laufzeit von `f(x)` relativ kleiner ist als die Kosten für das Starten und Synchronisieren einer Aufgabe (typischerweise weniger als 10 Mikrosekunden).

!!! compat "Julia 1.8"
    Die `:dynamic`-Option für das `schedule`-Argument ist seit Julia 1.8 verfügbar und der Standard.


### `:greedy`

Der `:greedy`-Scheduler startet bis zu [`Threads.threadpoolsize()`](@ref) Aufgaben, die jeweils gierig an den gegebenen iterierten Werten arbeiten, sobald sie produziert werden. Sobald eine Aufgabe ihre Arbeit beendet, nimmt sie den nächsten Wert aus dem Iterator. Die Arbeit, die von einer einzelnen Aufgabe erledigt wird, erfolgt nicht unbedingt an zusammenhängenden Werten aus dem Iterator. Der gegebene Iterator kann Werte für immer produzieren, es ist nur die Iterator-Schnittstelle erforderlich (kein Indizieren).

Diese Scheduling-Option ist im Allgemeinen eine gute Wahl, wenn die Arbeitslast der einzelnen Iterationen nicht gleichmäßig ist oder eine große Streuung aufweist.

!!! compat "Julia 1.11"
    Die `:greedy`-Option für das `schedule`-Argument ist seit Julia 1.11 verfügbar.


### `:static`

Der `:static`-Scheduler erstellt eine Aufgabe pro Thread und teilt die Iterationen gleichmäßig unter ihnen auf, wobei jeder Aufgabe spezifisch einem Thread zugewiesen wird. Insbesondere ist der Wert von [`threadid()`](@ref Threads.threadid) innerhalb einer Iteration konstant garantiert. Die Angabe von `:static` ist ein Fehler, wenn sie innerhalb einer anderen `@threads`-Schleife oder von einem anderen Thread als 1 verwendet wird.

!!! note
    Die `:static`-Planung existiert zur Unterstützung des Übergangs von Code, der vor Julia 1.3 geschrieben wurde. In neu geschriebenen Bibliotheksfunktionen wird von der `:static`-Planung abgeraten, da die Funktionen, die diese Option verwenden, nicht von beliebigen Arbeiter-Threads aufgerufen werden können.


## Beispiele

Um die verschiedenen Scheduling-Strategien zu veranschaulichen, betrachten Sie die folgende Funktion `busywait`, die eine nicht-yielding zeitgesteuerte Schleife enthält, die für eine bestimmte Anzahl von Sekunden läuft.

```julia-repl
julia> function busywait(seconds)
            tstart = time_ns()
            while (time_ns() - tstart) / 1e9 < seconds
            end
        end

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :static for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
6.003001 Sekunden (16.33 k Zuweisungen: 899.255 KiB, 0.25% Kompilierungszeit)

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :dynamic for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
2.012056 Sekunden (16.05 k Zuweisungen: 883.919 KiB, 0.66% Kompilierungszeit)
```

Das `:dynamic`-Beispiel benötigt 2 Sekunden, da einer der nicht besetzten Threads in der Lage ist, zwei der 1-Sekunden-Iterationen auszuführen, um die for-Schleife abzuschließen. ```

# [Asynchronous Programming](@id man-asynchronous)

Wenn ein Programm mit der Außenwelt interagieren muss, zum Beispiel mit einer anderen Maschine über das Internet kommunizieren, müssen Vorgänge im Programm möglicherweise in einer unvorhersehbaren Reihenfolge ablaufen. Angenommen, Ihr Programm muss eine Datei herunterladen. Wir möchten den Downloadvorgang initiieren, während wir auf den Abschluss warten, andere Vorgänge ausführen und dann den Code fortsetzen, der die heruntergeladene Datei benötigt, wenn sie verfügbar ist. Dieses Szenario fällt in den Bereich der asynchronen Programmierung, die manchmal auch als nebenläufige Programmierung bezeichnet wird (da konzeptionell mehrere Dinge gleichzeitig passieren).

Um diese Szenarien zu adressieren, bietet Julia [`Task`](@ref) (auch bekannt unter mehreren anderen Namen, wie symmetrische Koroutinen, leichte Threads, kooperatives Multitasking oder Einmal-Fortsetzungen). Wenn ein Stück Rechenarbeit (in der Praxis das Ausführen einer bestimmten Funktion) als `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` bezeichnet wird, wird es möglich, es zu unterbrechen, indem zu einem anderen `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` gewechselt wird. Der ursprüngliche `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` kann später wieder aufgenommen werden, wobei er genau dort weitermacht, wo er aufgehört hat. Zunächst mag dies einer Funktionsaufruf ähnlich erscheinen. Es gibt jedoch zwei wesentliche Unterschiede. Erstens verbraucht der Wechsel der Aufgaben keinen Speicher, sodass beliebig viele Aufgabenwechsel stattfinden können, ohne den Aufrufstapel zu beanspruchen. Zweitens kann der Wechsel zwischen Aufgaben in beliebiger Reihenfolge erfolgen, im Gegensatz zu Funktionsaufrufen, bei denen die aufgerufene Funktion abgeschlossen sein muss, bevor die Kontrolle zur aufrufenden Funktion zurückkehrt.

## Basic `Task` operations

Sie können sich eine `Task` als einen Verweis auf eine Einheit von zu erledigender Rechenarbeit vorstellen. Sie hat einen Lebenszyklus von Erstellen-Starten-Ausführen-Abschließen. Aufgaben werden erstellt, indem der `Task`-Konstruktor auf einer Funktion ohne Argumente aufgerufen wird, die ausgeführt werden soll, oder indem das [`@task`](@ref)-Makro verwendet wird:

```julia-repl
julia> t = @task begin; sleep(5); println("done"); end
Task (runnable) @0x00007f13a40c0eb0
```

`@task x` entspricht `Task(()->x)`.

Diese Aufgabe wird fünf Sekunden warten und dann `done` ausgeben. Sie hat jedoch noch nicht begonnen zu laufen. Wir können sie ausführen, wann immer wir bereit sind, indem wir [`schedule`](@ref) aufrufen:

```julia-repl
julia> schedule(t);
```

Wenn Sie dies im REPL ausprobieren, werden Sie sehen, dass `schedule` sofort zurückkehrt. Das liegt daran, dass es einfach `t` zu einer internen Warteschlange von Aufgaben hinzufügt, die ausgeführt werden sollen. Dann wird der REPL die nächste Eingabeaufforderung drucken und auf weitere Eingaben warten. Das Warten auf Tastatureingaben bietet die Möglichkeit, dass andere Aufgaben ausgeführt werden, sodass zu diesem Zeitpunkt `t` gestartet wird. `t` ruft [`sleep`](@ref) auf, was einen Timer setzt und die Ausführung stoppt. Wenn andere Aufgaben geplant wurden, könnten sie dann ausgeführt werden. Nach fünf Sekunden wird der Timer ausgelöst und `t` wird neu gestartet, und Sie werden `done` gedruckt sehen. `t` ist dann beendet.

Die [`wait`](@ref)-Funktion blockiert die aufrufende Aufgabe, bis eine andere Aufgabe abgeschlossen ist. Wenn Sie also beispielsweise eingeben

```julia-repl
julia> schedule(t); wait(t)
```

anstatt nur `schedule` aufzurufen, sehen Sie eine fünfsekündige Pause, bevor die nächste Eingabeaufforderung erscheint. Das liegt daran, dass die REPL darauf wartet, dass `t` abgeschlossen ist, bevor sie fortfährt.

Es ist üblich, eine Aufgabe zu erstellen und sie sofort zu planen, daher wird das Makro [`@async`](@ref) zu diesem Zweck bereitgestellt –- `@async x` entspricht `schedule(@task x)`.

## Communicating with Channels

In einigen Problemen sind die verschiedenen Teile der erforderlichen Arbeit nicht natürlich durch Funktionsaufrufe miteinander verbunden; es gibt keinen offensichtlichen "Aufrufer" oder "Aufgerufenen" unter den Aufgaben, die erledigt werden müssen. Ein Beispiel ist das Produzenten-Konsumenten-Problem, bei dem ein komplexes Verfahren Werte generiert und ein anderes komplexes Verfahren diese konsumiert. Der Konsument kann nicht einfach eine Produzentenfunktion aufrufen, um einen Wert zu erhalten, da der Produzent möglicherweise noch weitere Werte zu generieren hat und daher möglicherweise noch nicht bereit ist, zurückzugeben. Mit Aufgaben können Produzent und Konsument beide so lange laufen, wie sie benötigen, und Werte nach Bedarf hin und her übergeben.

Julia bietet einen [`Channel`](@ref) Mechanismus zur Lösung dieses Problems. Ein `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` ist eine wartbare First-In-First-Out-Warteschlange, die mehrere Aufgaben hat, die von ihr lesen und in sie schreiben können.

Lass uns eine Produzentenaufgabe definieren, die Werte über den [`put!`](@ref) Aufruf produziert. Um Werte zu konsumieren, müssen wir den Produzenten planen, um in einer neuen Aufgabe zu laufen. Ein spezieller [`Channel`](@ref) Konstruktor, der eine Funktion mit einem Argument als Argument akzeptiert, kann verwendet werden, um eine Aufgabe zu starten, die an einen Kanal gebunden ist. Wir können dann [`take!`](@ref) Werte wiederholt aus dem Kanalobjekt entnehmen:

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

Eine Möglichkeit, dieses Verhalten zu betrachten, ist, dass `producer` in der Lage war, mehrfach zurückzukehren. Zwischen den Aufrufen von [`put!`](@ref) wird die Ausführung des Producers ausgesetzt und der Consumer hat die Kontrolle.

Das zurückgegebene [`Channel`](@ref) kann als iterierbares Objekt in einer `for`-Schleife verwendet werden, wobei die Schleifenvariable alle erzeugten Werte annimmt. Die Schleife wird beendet, wenn der Kanal geschlossen wird.

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

Beachten Sie, dass wir den Kanal im Producer nicht explizit schließen mussten. Dies liegt daran, dass das Binden eines [`Channel`](@ref) an einen [`Task`](@ref) die offene Lebensdauer eines Kanals mit der des gebundenen Tasks verknüpft. Das Kanalobjekt wird automatisch geschlossen, wenn der Task beendet wird. Mehrere Kanäle können an einen Task gebunden werden und umgekehrt.

Während der [`Task`](@ref) Konstruktor eine Funktion ohne Argumente erwartet, erwartet die [`Channel`](@ref) Methode, die einen aufgabengebundenen Kanal erstellt, eine Funktion, die ein einzelnes Argument vom Typ `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` akzeptiert. Ein gängiges Muster ist, dass der Produzent parametrisiert ist, in diesem Fall ist eine partielle Funktionsanwendung erforderlich, um eine 0- oder 1-Argument [anonymous function](@ref man-anonymous-functions) zu erstellen.

Für [`Task`](@ref) Objekte kann dies entweder direkt oder durch die Verwendung eines Komfortmakros erfolgen:

```julia
function mytask(myarg)
    ...
end

taskHdl = Task(() -> mytask(7))
# or, equivalently
taskHdl = @task mytask(7)
```

Um fortgeschrittenere Arbeitsverteilungsmuster zu orchestrieren, können [`bind`](@ref) und [`schedule`](@ref) in Verbindung mit [`Task`](@ref) und [`Channel`](@ref) Konstruktoren verwendet werden, um explizit eine Menge von Kanälen mit einer Menge von Produzenten-/Konsumententasks zu verknüpfen.

### More on Channels

Ein Kanal kann als ein Rohr visualisiert werden, d.h. er hat ein Schreibende und ein Leseende:

  * Mehrere Autoren können in verschiedenen Aufgaben gleichzeitig über [`put!`](@ref)-Aufrufe in denselben Kanal schreiben.
  * Mehrere Leser in verschiedenen Aufgaben können Daten gleichzeitig über [`take!`](@ref)-Aufrufe lesen.
  * Als Beispiel:

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
  * Kanäle werden über den Konstruktor `Channel{T}(sz)` erstellt. Der Kanal kann nur Objekte vom Typ `T` halten. Wenn der Typ nicht angegeben ist, kann der Kanal Objekte beliebigen Typs halten. `sz` bezieht sich auf die maximale Anzahl von Elementen, die zu jedem Zeitpunkt im Kanal gehalten werden können. Zum Beispiel erstellt `Channel(32)` einen Kanal, der maximal 32 Objekte beliebigen Typs halten kann. Ein `Channel{MyType}(64)` kann zu jedem Zeitpunkt bis zu 64 Objekte vom Typ `MyType` halten.
  * Wenn ein [`Channel`](@ref) leer ist, werden die Leser (bei einem [`take!`](@ref) Aufruf) blockieren, bis Daten verfügbar sind.
  * Wenn ein [`Channel`](@ref) voll ist, werden die Schreiber (bei einem [`put!`](@ref) Aufruf) blockieren, bis wieder Platz verfügbar ist.
  * [`isready`](@ref) testet das Vorhandensein eines Objekts im Kanal, während [`wait`](@ref) darauf wartet, dass ein Objekt verfügbar wird.
  * Ein [`Channel`](@ref) befindet sich zunächst in einem offenen Zustand. Das bedeutet, dass es frei über [`take!`](@ref) und [`put!`](@ref) Aufrufe gelesen und beschrieben werden kann. [`close`](@ref) schließt ein `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`. Bei einem geschlossenen `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` wird `4d61726b646f776e2e436f64652822222c2022707574212229_40726566` fehlschlagen. Zum Beispiel:

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
  * [`take!`](@ref) und [`fetch`](@ref) (die den Wert abruft, aber nicht entfernt) geben in einem geschlossenen Kanal erfolgreich alle vorhandenen Werte zurück, bis er geleert ist. Fortsetzung des obigen Beispiels:

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

Betrachten Sie ein einfaches Beispiel für die Kommunikation zwischen Aufgaben mithilfe von Kanälen. Wir starten 4 Aufgaben, um Daten von einem einzelnen `jobs`-Kanal zu verarbeiten. Jobs, die durch eine ID (`job_id`) identifiziert werden, werden in den Kanal geschrieben. Jede Aufgabe in dieser Simulation liest eine `job_id`, wartet eine zufällige Zeit und schreibt ein Tupel aus `job_id` und der simulierten Zeit zurück in den Ergebniskanal. Schließlich werden alle `results` ausgegeben.

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

Statt `errormonitor(t)` könnte eine robustere Lösung die Verwendung von `bind(results, t)` sein, da dies nicht nur unerwartete Fehler protokolliert, sondern auch die zugehörigen Ressourcen schließt und die Ausnahme überall propagiert.

## More task operations

Aufgabenoperationen basieren auf einem Low-Level-Primitive namens [`yieldto`](@ref). `yieldto(task, value)` unterbricht die aktuelle Aufgabe, wechselt zur angegebenen `task` und bewirkt, dass der letzte `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566`-Aufruf dieser Aufgabe den angegebenen `value` zurückgibt. Beachten Sie, dass `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` die einzige Operation ist, die erforderlich ist, um den aufgabenbasierten Kontrollfluss zu verwenden; anstelle von Aufrufen und Rückgaben wechseln wir immer nur zu einer anderen Aufgabe. Aus diesem Grund wird dieses Feature auch als "symmetrische Koroutinen" bezeichnet; jede Aufgabe wird mit demselben Mechanismus gewechselt.

[`yieldto`](@ref) ist leistungsstark, aber die meisten Verwendungen von Aufgaben rufen es nicht direkt auf. Überlegen Sie, warum das so sein könnte. Wenn Sie von der aktuellen Aufgabe wechseln, möchten Sie wahrscheinlich irgendwann wieder zu ihr zurückkehren, aber zu wissen, wann man zurückwechseln sollte und welche Aufgabe die Verantwortung für den Rückwechsel hat, kann erhebliche Koordination erfordern. Zum Beispiel sind [`put!`](@ref) und [`take!`](@ref) blockierende Operationen, die, wenn sie im Kontext von Kanälen verwendet werden, den Zustand beibehalten, um sich daran zu erinnern, wer die Verbraucher sind. Nicht manuell nachverfolgen zu müssen, welche Aufgabe konsumiert, macht `4d61726b646f776e2e436f64652822222c2022707574212229_40726566` einfacher zu verwenden als das niedrigere `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566`.

Zusätzlich zu [`yieldto`](@ref) sind einige andere grundlegende Funktionen erforderlich, um Aufgaben effektiv zu nutzen.

  * [`current_task`](@ref) erhält eine Referenz auf die derzeit laufende Aufgabe.
  * [`istaskdone`](@ref) fragt, ob eine Aufgabe beendet wurde.
  * [`istaskstarted`](@ref) fragt, ob eine Aufgabe bereits ausgeführt wurde.
  * [`task_local_storage`](@ref) manipuliert einen schlüssel-wert-speicher, der spezifisch für die aktuelle Aufgabe ist.

## Tasks and events

Die meisten Aufgabenwechsel erfolgen aufgrund des Wartens auf Ereignisse wie I/O-Anfragen und werden von einem Scheduler in Julia Base durchgeführt. Der Scheduler verwaltet eine Warteschlange von ausführbaren Aufgaben und führt eine Ereignisschleife aus, die Aufgaben basierend auf externen Ereignissen wie dem Eintreffen von Nachrichten neu startet.

The basic function for waiting for an event is [`wait`](@ref). Several objects implement [`wait`](@ref); for example, given a `Process` object, [`wait`](@ref) will wait for it to exit. [`wait`](@ref) is often implicit; for example, a [`wait`](@ref) can happen inside a call to [`read`](@ref) to wait for data to be available.

In all diesen Fällen arbeitet [`wait`](@ref) letztendlich auf einem [`Condition`](@ref) Objekt, das für das Queuing und Neustarten von Aufgaben verantwortlich ist. Wenn eine Aufgabe `4d61726b646f776e2e436f64652822222c2022776169742229_40726566` auf einem `4d61726b646f776e2e436f64652822222c2022436f6e646974696f6e2229_40726566` aufruft, wird die Aufgabe als nicht ausführbar markiert, in die Warteschlange der Bedingung eingefügt und wechselt zum Scheduler. Der Scheduler wird dann eine andere Aufgabe auswählen, die ausgeführt werden soll, oder blockiert warten auf externe Ereignisse. Wenn alles gut geht, wird schließlich ein Ereignishandler [`notify`](@ref) auf der Bedingung aufrufen, was dazu führt, dass Aufgaben, die auf diese Bedingung warten, wieder ausführbar werden.

Eine Aufgabe, die ausdrücklich durch den Aufruf [`Task`](@ref) erstellt wurde, ist zunächst dem Scheduler nicht bekannt. Dies ermöglicht es Ihnen, Aufgaben manuell mit [`yieldto`](@ref) zu verwalten, wenn Sie dies wünschen. Wenn eine solche Aufgabe jedoch auf ein Ereignis wartet, wird sie dennoch automatisch neu gestartet, wenn das Ereignis eintritt, wie Sie es erwarten würden.

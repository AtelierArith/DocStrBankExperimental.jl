# [Multi-Threading](@id man-multithreading)

Besuchen Sie diese [blog post](https://julialang.org/blog/2019/07/multithreading/) für eine Präsentation der Multi-Threading-Funktionen von Julia.

## Starting Julia with multiple threads

Standardmäßig startet Julia mit einem einzelnen Ausführungsthread. Dies kann mit dem Befehl [`Threads.nthreads()`](@ref) überprüft werden:

```jldoctest
julia> Threads.nthreads()
1
```

Die Anzahl der Ausführungsthreads wird entweder durch die Verwendung des Befehlszeilenarguments `-t`/`--threads` oder durch die Verwendung der Umgebungsvariable [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) gesteuert. Wenn beide angegeben sind, hat `-t`/`--threads` Vorrang.

Die Anzahl der Threads kann entweder als Ganzzahl (`--threads=4`) oder als `auto` (`--threads=auto`) angegeben werden, wobei `auto` versucht, eine nützliche Standardanzahl von Threads zu ermitteln (siehe [Command-line Options](@ref command-line-interface) für weitere Details).

!!! compat "Julia 1.5"
    Das `-t`/`--threads` Befehlszeilenargument erfordert mindestens Julia 1.5. In älteren Versionen müssen Sie stattdessen die Umgebungsvariable verwenden.


!!! compat "Julia 1.7"
    Die Verwendung von `auto` als Wert der Umgebungsvariable [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) erfordert mindestens Julia 1.7. In älteren Versionen wird dieser Wert ignoriert.


Lass uns Julia mit 4 Threads starten:

```bash
$ julia --threads 4
```

Lass uns überprüfen, ob wir 4 Threads zur Verfügung haben.

```julia-repl
julia> Threads.nthreads()
4
```

Aber wir befinden uns derzeit im Master-Thread. Um dies zu überprüfen, verwenden wir die Funktion [`Threads.threadid`](@ref)

```jldoctest
julia> Threads.threadid()
1
```

!!! note
    Wenn Sie die Umgebungsvariable bevorzugen, können Sie sie wie folgt in Bash (Linux/macOS) festlegen:

    ```bash
    export JULIA_NUM_THREADS=4
    ```

    C-Shell unter Linux/macOS, CMD unter Windows:

    ```bash
    set JULIA_NUM_THREADS=4
    ```

    Powershell auf Windows:

    ```powershell
    $env:JULIA_NUM_THREADS=4
    ```

    Beachten Sie, dass dies *vor* dem Starten von Julia erledigt werden muss.


!!! note
    Die Anzahl der mit `-t`/`--threads` angegebenen Threads wird an die Arbeitsprozesse weitergegeben, die mit den Befehlszeilenoptionen `-p`/`--procs` oder `--machine-file` gestartet werden. Zum Beispiel startet `julia -p2 -t2` 1 Hauptprozess mit 2 Arbeitsprozessen, und alle drei Prozesse haben 2 aktivierte Threads. Für eine genauere Steuerung der Arbeits-Threads verwenden Sie [`addprocs`](@ref) und übergeben Sie `-t`/`--threads` als `exeflags`.


### Multiple GC Threads

Der Garbage Collector (GC) kann mehrere Threads verwenden. Die Anzahl der verwendeten Threads beträgt entweder die Hälfte der Anzahl der Rechen-Worker-Threads oder wird durch das `--gcthreads`-Befehlszeilenargument oder durch die Verwendung der [`JULIA_NUM_GC_THREADS`](@ref JULIA_NUM_GC_THREADS)-Umgebungsvariable konfiguriert.

!!! compat "Julia 1.10"
    Das `--gcthreads` Befehlszeilenargument erfordert mindestens Julia 1.10.


## [Threadpools](@id man-threadpools)

Wenn die Threads eines Programms mit vielen Aufgaben beschäftigt sind, können Aufgaben Verzögerungen erfahren, die sich negativ auf die Reaktionsfähigkeit und Interaktivität des Programms auswirken können. Um dies zu beheben, können Sie angeben, dass eine Aufgabe interaktiv ist, wenn Sie [`Threads.@spawn`](@ref) es:

```julia
using Base.Threads
@spawn :interactive f()
```

Interaktive Aufgaben sollten vermeiden, hochlatente Operationen durchzuführen, und wenn es sich um langandauernde Aufgaben handelt, sollten sie häufig unterbrechen.

Julia kann mit einem oder mehreren Threads gestartet werden, die für die Ausführung interaktiver Aufgaben reserviert sind:

```bash
$ julia --threads 3,1
```

Die Umgebungsvariable [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) kann auch ähnlich verwendet werden:

```bash
export JULIA_NUM_THREADS=3,1
```

Dies startet Julia mit 3 Threads im `:default` Threadpool und 1 Thread im `:interactive` Threadpool:

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
    Die Null-Argument-Version von `nthreads` gibt die Anzahl der Threads im Standard-Pool zurück.


!!! note
    Je nachdem, ob Julia mit interaktiven Threads gestartet wurde, befindet sich der Hauptthread entweder im Standard- oder im interaktiven Thread-Pool.


Entweder oder beide Zahlen können durch das Wort `auto` ersetzt werden, was dazu führt, dass Julia eine angemessene Standardwahl trifft.

## The `@threads` Macro

Lass uns ein einfaches Beispiel mit unseren nativen Threads erstellen. Lassen Sie uns ein Array von Nullen erstellen:

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

Lass uns dieses Array gleichzeitig mit 4 Threads bearbeiten. Jeder Thread wird seine Thread-ID in jede Position schreiben.

Julia unterstützt parallele Schleifen mit dem [`Threads.@threads`](@ref) Makro. Dieses Makro wird vor einer `for`-Schleife angebracht, um Julia anzuzeigen, dass die Schleife ein Multi-Thread-Bereich ist:

```julia-repl
julia> Threads.@threads for i = 1:10
           a[i] = Threads.threadid()
       end
```

Der Iterationsraum wird unter den Threads aufgeteilt, wonach jeder Thread seine Thread-ID an den zugewiesenen Stellen schreibt:

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

Beachten Sie, dass [`Threads.@threads`](@ref) keinen optionalen Reduktionsparameter hat, wie [`@distributed`](@ref).

### Using `@threads` without data-races

Das Konzept eines Datenrennens wird in ["Communication and data races between threads"](@ref man-communication-and-data-races) näher erläutert. Für den Moment sollten Sie nur wissen, dass ein Datenrennen zu falschen Ergebnissen und gefährlichen Fehlern führen kann.

Lass uns sagen, wir möchten die Funktion `sum_single` unten mehrthreadig machen.

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

Einfaches Hinzufügen von `@threads` führt zu einem Datenrennen, bei dem mehrere Threads gleichzeitig `s` lesen und schreiben.

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

Beachten Sie, dass das Ergebnis nicht `500000500000` ist, wie es sein sollte, und sich bei jeder Auswertung höchstwahrscheinlich ändern wird.

Um dies zu beheben, können spezifische Puffer für die Aufgabe verwendet werden, um die Summe in abschnittsweise, die frei von Rennen sind, zu segmentieren. Hier wird `sum_single` wiederverwendet, mit seinem eigenen internen Puffer `s`. Der Eingangsvektor `a` wird in `nthreads()` Abschnitte für parallele Arbeiten aufgeteilt. Wir verwenden dann `Threads.@spawn`, um Aufgaben zu erstellen, die jeweils jeden Abschnitt summieren. Schließlich summieren wir die Ergebnisse aus jeder Aufgabe erneut mit `sum_single`:

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
    Puffer sollten nicht basierend auf `threadid()` verwaltet werden, d.h. `buffers = zeros(Threads.nthreads())`, da konkurrierende Aufgaben yielden können, was bedeutet, dass mehrere konkurrierende Aufgaben denselben Puffer auf einem bestimmten Thread verwenden können, was das Risiko von Datenrennen erhöht. Darüber hinaus können Aufgaben, wenn mehr als ein Thread verfügbar ist, an den Yield-Punkten den Thread wechseln, was als [task migration](@ref man-task-migration) bekannt ist.


Eine weitere Option ist die Verwendung von atomaren Operationen auf Variablen, die zwischen Aufgaben/Threads geteilt werden, was je nach den Eigenschaften der Operationen leistungsfähiger sein kann.

## [Communication and data-races between threads](@id man-communication-and-data-races)

Obwohl Julias Threads über gemeinsamen Speicher kommunizieren können, ist es notorisch schwierig, korrekten und datarace-freien Multithread-Code zu schreiben. Julias [`Channel`](@ref) sind threadsicher und können sicher zur Kommunikation verwendet werden. Es gibt auch Abschnitte unten, die erklären, wie man [locks](@ref man-using-locks) und [atomics](@ref man-atomic-operations) verwendet, um Datenrennen zu vermeiden.

### Data-race freedom

Sie sind vollständig verantwortlich dafür, dass Ihr Programm frei von Datenrennen ist, und nichts, was hier versprochen wird, kann angenommen werden, wenn Sie diese Anforderung nicht beachten. Die beobachteten Ergebnisse können äußerst unintuitiv sein.

Wenn Datenrennen eingeführt werden, ist Julia nicht speichersicher. **Seien Sie sehr vorsichtig beim Lesen *irgendwelcher* Daten, wenn ein anderer Thread möglicherweise darauf schreibt, da dies zu Segmentierungsfehlern oder Schlimmerem führen könnte**. Im Folgenden sind einige unsichere Möglichkeiten aufgeführt, um von verschiedenen Threads auf globale Variablen zuzugreifen:

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

Ein wichtiges Werkzeug, um Datenrennen zu vermeiden und somit threadsicheren Code zu schreiben, ist das Konzept eines "Locks". Ein Lock kann gesperrt und entsperrt werden. Wenn ein Thread ein Lock gesperrt hat und es nicht entsperrt, wird gesagt, dass er das Lock "hält". Wenn es nur ein Lock gibt und wir Code schreiben, der das Halten des Locks erfordert, um auf einige Daten zuzugreifen, können wir sicherstellen, dass mehrere Threads niemals gleichzeitig auf dieselben Daten zugreifen. Beachten Sie, dass die Verbindung zwischen einem Lock und einer Variablen vom Programmierer und nicht vom Programm hergestellt wird.

Zum Beispiel können wir ein Schloss `my_lock` erstellen und es sperren, während wir eine Variable `my_variable` ändern. Dies geschieht am einfachsten mit dem `@lock`-Makro:

```julia-repl
julia> my_lock = ReentrantLock();

julia> my_variable = [1, 2, 3];

julia> @lock my_lock my_variable[1] = 100
100
```

Durch die Verwendung eines ähnlichen Musters mit demselben Lock und derselben Variablen, jedoch in einem anderen Thread, sind die Operationen frei von Datenrennen.

Wir hätten die oben beschriebene Operation mit der funktionalen Version von `lock` auf die folgenden zwei Arten durchführen können:

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

Alle drei Optionen sind gleichwertig. Beachten Sie, dass die endgültige Version einen expliziten `try`-Block erfordert, um sicherzustellen, dass das Lock immer entsperrt wird, während die ersten beiden Versionen dies intern tun. Man sollte immer das oben beschriebene Lock-Muster verwenden, wenn Daten geändert werden (wie das Zuweisen zu einer globalen oder Closure-Variablen), die von anderen Threads zugegriffen werden. Das Versäumnis, dies zu tun, könnte unvorhergesehene und schwerwiegende Folgen haben.

### [Atomic Operations](@id man-atomic-operations)

Julia unterstützt den Zugriff auf und die Modifikation von Werten *atomar*, das heißt, auf thread-sichere Weise, um [race conditions](https://en.wikipedia.org/wiki/Race_condition) zu vermeiden. Ein Wert (der vom primitiven Typ sein muss) kann als [`Threads.Atomic`](@ref) eingewickelt werden, um anzuzeigen, dass er auf diese Weise zugegriffen werden muss. Hier sehen wir ein Beispiel:

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

Hätten wir versucht, die Addition ohne das atomare Tag durchzuführen, hätten wir möglicherweise die falsche Antwort aufgrund einer Wettlaufbedingung erhalten. Ein Beispiel dafür, was passieren würde, wenn wir die Wettlaufbedingung nicht vermeiden würden:

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

Wir können auch Atomics auf einer granulareren Ebene verwenden, indem wir die [`@atomic`](@ref Base.@atomic), [`@atomicswap`](@ref Base.@atomicswap), [`@atomicreplace`](@ref Base.@atomicreplace) Makros und [`@atomiconce`](@ref Base.@atomiconce) Makros.

Spezifische Details des Speichermodells und andere Details des Designs sind in der [Julia Atomics Manifesto](https://gist.github.com/vtjnash/11b0031f2e2a66c9c24d33e810b34ec0) geschrieben, die später formell veröffentlicht werden.

Jedes Feld in einer Strukturdeklaration kann mit `@atomic` dekoriert werden, und dann muss jeder Schreibvorgang ebenfalls mit `@atomic` gekennzeichnet werden und eine der definierten atomaren Ordnungen verwenden (`:monotonic`, `:acquire`, `:release`, `:acquire_release` oder `:sequentially_consistent`). Jeder Lesevorgang eines atomaren Feldes kann ebenfalls mit einer atomaren Ordnungsbeschränkung annotiert werden oder wird mit monotoner (entspannter) Ordnung durchgeführt, wenn nicht angegeben.

!!! compat "Julia 1.7"
    Per-Field-Atomics erfordert mindestens Julia 1.7.


## Side effects and mutable function arguments

Beim Einsatz von Multi-Threading müssen wir vorsichtig sein, wenn wir Funktionen verwenden, die nicht [pure](https://en.wikipedia.org/wiki/Pure_function) sind, da wir sonst eine falsche Antwort erhalten könnten. Zum Beispiel haben Funktionen, die eine [name ending with `!`](@ref bang-convention) haben, nach Konvention die Eigenschaft, ihre Argumente zu modifizieren und sind somit nicht rein.

## @threadcall

Externe Bibliotheken, wie die, die über [`ccall`](@ref) aufgerufen werden, stellen ein Problem für Julias aufgabenbasierten I/O-Mechanismus dar. Wenn eine C-Bibliothek eine blockierende Operation ausführt, verhindert dies, dass der Julia-Scheduler andere Aufgaben ausführt, bis der Aufruf zurückkehrt. (Ausnahmen sind Aufrufe in benutzerdefinierten C-Code, die in Julia zurückrufen, was dann yielden kann, oder C-Code, der `jl_yield()` aufruft, das C-Äquivalent von [`yield`](@ref).)

Das [`@threadcall`](@ref) Makro bietet eine Möglichkeit, das Ausführen in einem solchen Szenario zu vermeiden. Es plant eine C-Funktion zur Ausführung in einem separaten Thread. Ein Threadpool mit einer Standardgröße von 4 wird dafür verwendet. Die Größe des Threadpools wird über die Umgebungsvariable `UV_THREADPOOL_SIZE` gesteuert. Während auf einen freien Thread gewartet wird und während der Funktionsausführung, sobald ein Thread verfügbar ist, gibt die anfordernde Aufgabe (im Haupt-Julia-Ereignisloop) anderen Aufgaben nach. Beachten Sie, dass `@threadcall` nicht zurückkehrt, bis die Ausführung abgeschlossen ist. Aus der Sicht des Benutzers handelt es sich daher um einen blockierenden Aufruf wie bei anderen Julia-APIs.

Es ist sehr wichtig, dass die aufgerufene Funktion nicht in Julia zurückruft, da dies zu einem Segfault führen wird.

`@threadcall` könnte in zukünftigen Versionen von Julia entfernt oder geändert werden.

## Caveats

Zu diesem Zeitpunkt können die meisten Operationen in der Julia-Laufzeit und den Standardbibliotheken auf thread-sichere Weise verwendet werden, wenn der Benutzercode rennbedingungsfrei ist. In einigen Bereichen wird jedoch weiterhin an der Stabilisierung der Thread-Unterstützung gearbeitet. Die mehrfädige Programmierung hat viele inhärente Schwierigkeiten, und wenn ein Programm, das Threads verwendet, ungewöhnliches oder unerwünschtes Verhalten zeigt (z. B. Abstürze oder mysteriöse Ergebnisse), sollten in der Regel zuerst die Interaktionen zwischen den Threads verdächtigt werden.

Es gibt einige spezifische Einschränkungen und Warnungen, die beim Verwenden von Threads in Julia zu beachten sind:

  * Basis-Kollektionstypen erfordern manuelles Sperren, wenn sie gleichzeitig von mehreren Threads verwendet werden, wobei mindestens ein Thread die Sammlung ändert (häufige Beispiele sind `push!` auf Arrays oder das Einfügen von Elementen in ein `Dict`).
  * Der Zeitplan, der von [`@spawn`](@ref Threads.@spawn) verwendet wird, ist nicht deterministisch und sollte nicht als zuverlässig angesehen werden.
  * Rechenintensive, nicht speicherallokierende Aufgaben können verhindern, dass die Garbage Collection in anderen Threads, die Speicher allokieren, ausgeführt wird. In diesen Fällen kann es notwendig sein, einen manuellen Aufruf von `GC.safepoint()` einzufügen, um der Garbage Collection zu ermöglichen, ausgeführt zu werden. Diese Einschränkung wird in Zukunft aufgehoben.
  * Vermeiden Sie das gleichzeitige Ausführen von Operationen auf oberster Ebene, z. B. `include` oder `eval` von Typ-, Methoden- und Moduldifinitionen.
  * Seien Sie sich bewusst, dass Finalizer, die von einer Bibliothek registriert wurden, brechen können, wenn Threads aktiviert sind. Dies kann einige Übergangsarbeiten im gesamten Ökosystem erfordern, bevor Multithreading mit Vertrauen weit verbreitet angenommen werden kann. Siehe den Abschnitt über [the safe use of finalizers](@ref man-finalizers) für weitere Details.

## [Task Migration](@id man-task-migration)

Nachdem eine Aufgabe auf einem bestimmten Thread gestartet wurde, kann sie zu einem anderen Thread wechseln, wenn die Aufgabe aufgibt.

Solche Aufgaben könnten mit [`@spawn`](@ref Threads.@spawn) oder [`@threads`](@ref Threads.@threads) begonnen worden sein, obwohl die `:static` Zeitplanoption für `@threads` die threadid einfriert.

Das bedeutet, dass in den meisten Fällen [`threadid()`](@ref Threads.threadid) nicht als konstant innerhalb einer Aufgabe behandelt werden sollte und daher nicht verwendet werden sollte, um in einen Vektor von Puffern oder zustandsbehafteten Objekten zu indizieren.

!!! compat "Julia 1.7"
    Die Aufgabenmigration wurde in Julia 1.7 eingeführt. Zuvor blieben diese Aufgaben immer auf dem gleichen Thread, auf dem sie gestartet wurden.


## [Safe use of Finalizers](@id man-finalizers)

Weil Finalisierer jeden Code unterbrechen können, müssen sie sehr vorsichtig sein, wie sie mit globalem Zustand interagieren. Leider ist der Hauptgrund, warum Finalisierer verwendet werden, um den globalen Zustand zu aktualisieren (eine reine Funktion ist im Allgemeinen als Finalisierer eher sinnlos). Das führt uns zu einem kleinen Dilemma. Es gibt einige Ansätze, um mit diesem Problem umzugehen:

1. Wenn der Code einsträngig ist, könnte er die interne C-Funktion `jl_gc_enable_finalizers` aufrufen, um zu verhindern, dass Finalisierer innerhalb eines kritischen Bereichs geplant werden. Intern wird dies in einigen Funktionen (wie unseren C-Sperren) verwendet, um Rekursionen bei bestimmten Operationen (inkrementelles Laden von Paketen, Codegenerierung usw.) zu verhindern. Die Kombination aus einer Sperre und diesem Flag kann verwendet werden, um Finalisierer sicher zu machen.
2. Eine zweite Strategie, die von Base an einigen Stellen verwendet wird, besteht darin, einen Finalizer ausdrücklich zu verzögern, bis er möglicherweise in der Lage ist, sein Lock nicht rekursiv zu erwerben. Das folgende Beispiel zeigt, wie diese Strategie auf `Distributed.finalize_ref` angewendet werden könnte:

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
3. Eine verwandte dritte Strategie besteht darin, eine wartungsfreie Warteschlange zu verwenden. Wir haben derzeit keine lockfreie Warteschlange in Base implementiert, aber `Base.IntrusiveLinkedListSynchronized{T}` ist geeignet. Dies kann häufig eine gute Strategie für Code mit Ereignisschleifen sein. Zum Beispiel wird diese Strategie von `Gtk.jl` verwendet, um die Lebensdauer der Referenzzählung zu verwalten. In diesem Ansatz führen wir keine explizite Arbeit innerhalb des `finalizer` aus, sondern fügen sie einer Warteschlange hinzu, um sie zu einem sichereren Zeitpunkt auszuführen. Tatsächlich verwendet Julias Aufgabenplaner dies bereits, sodass die Definition des Finalizers als `x -> @spawn do_cleanup(x)` ein Beispiel für diesen Ansatz ist. Beachten Sie jedoch, dass dies nicht steuert, auf welchem Thread `do_cleanup` ausgeführt wird, sodass `do_cleanup` weiterhin ein Lock erwerben müsste. Das muss nicht der Fall sein, wenn Sie Ihre eigene Warteschlange implementieren, da Sie diese Warteschlange explizit nur von Ihrem Thread entleeren können.

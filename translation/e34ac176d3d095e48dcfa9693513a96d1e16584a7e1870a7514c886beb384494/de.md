# Multi-processing and Distributed Computing

Eine Implementierung des parallelen Rechnens mit verteiltem Speicher wird durch das Modul [`Distributed`](@ref man-distributed) als Teil der Standardbibliothek, die mit Julia geliefert wird, bereitgestellt.

Die meisten modernen Computer verfügen über mehr als eine CPU, und mehrere Computer können in einem Cluster zusammengefasst werden. Die Nutzung der Leistung dieser mehreren CPUs ermöglicht es, viele Berechnungen schneller abzuschließen. Es gibt zwei Hauptfaktoren, die die Leistung beeinflussen: die Geschwindigkeit der CPUs selbst und die Geschwindigkeit ihres Zugriffs auf den Speicher. In einem Cluster ist es ziemlich offensichtlich, dass eine bestimmte CPU den schnellsten Zugriff auf den RAM innerhalb desselben Computers (Knotens) hat. Vielleicht überraschenderweise sind ähnliche Probleme auch bei einem typischen Multicore-Laptop relevant, aufgrund von Unterschieden in der Geschwindigkeit des Hauptspeichers und der [cache](https://www.akkadia.org/drepper/cpumemory.pdf). Folglich sollte eine gute Multiprocessing-Umgebung die Kontrolle über das "Eigentum" eines Speicherbereichs durch eine bestimmte CPU ermöglichen. Julia bietet eine Multiprocessing-Umgebung, die auf Nachrichtenübertragung basiert, um es Programmen zu ermöglichen, gleichzeitig auf mehreren Prozessen in separaten Speicherdomänen zu laufen.

Julias Implementierung der Nachrichtenübertragung unterscheidet sich von anderen Umgebungen wie MPI[^1]. Die Kommunikation in Julia ist im Allgemeinen "einseitig", was bedeutet, dass der Programmierer nur einen Prozess in einer Zwei-Prozess-Operation explizit verwalten muss. Darüber hinaus sehen diese Operationen typischerweise nicht wie "Nachricht senden" und "Nachricht empfangen" aus, sondern ähneln eher höherstufigen Operationen wie Aufrufen von Benutzerfunktionen.

Verteilte Programmierung in Julia basiert auf zwei Primitiven: *remote references* und *remote calls*. Eine remote reference ist ein Objekt, das von jedem Prozess verwendet werden kann, um auf ein Objekt zu verweisen, das auf einem bestimmten Prozess gespeichert ist. Ein remote call ist eine Anfrage eines Prozesses, eine bestimmte Funktion mit bestimmten Argumenten auf einem anderen (möglicherweise dem gleichen) Prozess aufzurufen.

Remote-Referenzen kommen in zwei Varianten: [`Future`](@ref Distributed.Future) und [`RemoteChannel`](@ref).

Ein Remote-Call gibt [`Future`](@ref Distributed.Future) als Ergebnis zurück. Remote-Calls geben sofort zurück; der Prozess, der den Call gemacht hat, fährt mit seiner nächsten Operation fort, während der Remote-Call irgendwo anders stattfindet. Sie können auf das Ende eines Remote-Calls warten, indem Sie [`wait`](@ref) auf dem zurückgegebenen `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` aufrufen, und Sie können den vollständigen Wert des Ergebnisses mit [`fetch`](@ref) erhalten.

Andererseits sind [`RemoteChannel`](@ref) schreibbar. Zum Beispiel können mehrere Prozesse ihre Verarbeitung koordinieren, indem sie auf dasselbe entfernte `Channel` verweisen.

Jeder Prozess hat eine zugehörige Kennung. Der Prozess, der die interaktive Julia-Eingabeaufforderung bereitstellt, hat immer eine `id`, die gleich 1 ist. Die standardmäßig für parallele Operationen verwendeten Prozesse werden als "Arbeiter" bezeichnet. Wenn es nur einen Prozess gibt, wird Prozess 1 als Arbeiter betrachtet. Andernfalls werden alle Prozesse außer Prozess 1 als Arbeiter betrachtet. Daher ist es erforderlich, 2 oder mehr Prozesse hinzuzufügen, um von parallelen Verarbeitungsmethoden wie [`pmap`](@ref) zu profitieren. Das Hinzufügen eines einzelnen Prozesses ist vorteilhaft, wenn Sie einfach andere Dinge im Hauptprozess tun möchten, während eine lange Berechnung auf dem Arbeiter läuft.

Lass uns das ausprobieren. Mit `julia -p n` werden `n` Arbeitsprozesse auf der lokalen Maschine bereitgestellt. Im Allgemeinen ist es sinnvoll, dass `n` der Anzahl der CPU-Threads (logische Kerne) auf der Maschine entspricht. Beachten Sie, dass das Argument `-p` das Modul [`Distributed`](@ref man-distributed) implizit lädt.

```julia
$ julia -p 2

julia> r = remotecall(rand, 2, 2, 2)
Future(2, 1, 4, nothing)

julia> s = @spawnat 2 1 .+ fetch(r)
Future(2, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.18526  1.50912
 1.16296  1.60607
```

Das erste Argument zu [`remotecall`](@ref) ist die Funktion, die aufgerufen werden soll. Die meisten parallelen Programmierungen in Julia beziehen sich nicht auf spezifische Prozesse oder die Anzahl der verfügbaren Prozesse, aber `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` wird als eine Low-Level-Schnittstelle betrachtet, die eine feinere Kontrolle bietet. Das zweite Argument zu `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` ist die `id` des Prozesses, der die Arbeit verrichten wird, und die verbleibenden Argumente werden an die aufgerufene Funktion übergeben.

Wie Sie sehen können, haben wir in der ersten Zeile Prozess 2 gebeten, eine 2x2-Zufallsmatrix zu erstellen, und in der zweiten Zeile haben wir ihn gebeten, 1 hinzuzufügen. Das Ergebnis beider Berechnungen ist in den beiden Futures `r` und `s` verfügbar. Das [`@spawnat`](@ref)-Makro wertet den Ausdruck im zweiten Argument im Prozess aus, der im ersten Argument angegeben ist.

Gelegentlich möchten Sie möglicherweise einen sofort berechneten Wert aus der Ferne. Dies geschieht typischerweise, wenn Sie von einem Remote-Objekt lesen, um Daten zu erhalten, die für die nächste lokale Operation benötigt werden. Die Funktion [`remotecall_fetch`](@ref) existiert zu diesem Zweck. Sie ist äquivalent zu `fetch(remotecall(...))`, ist jedoch effizienter.

```julia-repl
julia> remotecall_fetch(r-> fetch(r)[1, 1], 2, r)
0.18526337335308085
```

Dies ruft das Array auf Worker 2 ab und gibt den ersten Wert zurück. Beachten Sie, dass `fetch` in diesem Fall keine Daten verschiebt, da es auf dem Worker ausgeführt wird, der das Array besitzt. Man kann auch schreiben:

```julia-repl
julia> remotecall_fetch(getindex, 2, r, 1, 1)
0.10824216411304866
```

Denke daran, dass [`getindex(r,1,1)`](@ref) [equivalent](@ref man-array-indexing) zu `r[1,1]` ist, sodass dieser Aufruf das erste Element der zukünftigen `r` abruft.

Um die Dinge einfacher zu machen, kann das Symbol `:any` an [`@spawnat`](@ref) übergeben werden, das auswählt, wo die Operation für Sie durchgeführt werden soll:

```julia-repl
julia> r = @spawnat :any rand(2,2)
Future(2, 1, 4, nothing)

julia> s = @spawnat :any 1 .+ fetch(r)
Future(3, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.38854  1.9098
 1.20939  1.57158
```

Beachten Sie, dass wir `1 .+ fetch(r)` anstelle von `1 .+ r` verwendet haben. Dies liegt daran, dass wir nicht wissen, wo der Code ausgeführt wird, sodass im Allgemeinen ein [`fetch`](@ref) erforderlich sein könnte, um `r` an den Prozess zu übergeben, der die Addition durchführt. In diesem Fall ist [`@spawnat`](@ref) intelligent genug, um die Berechnung im Prozess durchzuführen, der `r` besitzt, sodass `4d61726b646f776e2e436f64652822222c202266657463682229_40726566` ein No-Op (es wird keine Arbeit verrichtet) sein wird.

(Es ist erwähnenswert, dass [`@spawnat`](@ref) nicht eingebaut, sondern in Julia als [macro](@ref man-macros) definiert ist. Es ist möglich, eigene solche Konstrukte zu definieren.)

Eine wichtige Sache, die man sich merken sollte, ist, dass, sobald ein [`Future`](@ref Distributed.Future) abgerufen wurde, sein Wert lokal zwischengespeichert wird. Weitere [`fetch`](@ref) Aufrufe erfordern keinen Netzwerk-Hit. Sobald alle referenzierenden `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`s abgerufen wurden, wird der remote gespeicherte Wert gelöscht.

[`@async`](@ref) ist ähnlich wie [`@spawnat`](@ref), führt jedoch Aufgaben nur im lokalen Prozess aus. Wir verwenden es, um eine "Feeder"-Aufgabe für jeden Prozess zu erstellen. Jede Aufgabe wählt den nächsten Index aus, der berechnet werden muss, wartet dann, bis ihr Prozess abgeschlossen ist, und wiederholt dies, bis wir keine Indizes mehr haben. Beachten Sie, dass die Feeder-Aufgaben nicht mit der Ausführung beginnen, bis die Hauptaufgabe das Ende des [`@sync`](@ref)-Blocks erreicht, an dem Punkt gibt sie die Kontrolle ab und wartet darauf, dass alle lokalen Aufgaben abgeschlossen sind, bevor sie aus der Funktion zurückkehrt. Was v0.7 und darüber hinaus betrifft, können die Feeder-Aufgaben den Zustand über `nextidx` teilen, da sie alle im selben Prozess ausgeführt werden. Selbst wenn `Tasks` kooperativ geplant sind, kann in einigen Kontexten eine Sperrung erforderlich sein, wie in [asynchronous I/O](@ref faq-async-io). Das bedeutet, dass Kontextwechsel nur an gut definierten Punkten stattfinden: in diesem Fall, wenn [`remotecall_fetch`](@ref) aufgerufen wird. Dies ist der aktuelle Stand der Implementierung und kann sich in zukünftigen Julia-Versionen ändern, da es beabsichtigt ist, bis zu N `Tasks` auf M `Process` auszuführen, auch bekannt als [M:N Threading](https://en.wikipedia.org/wiki/Thread_(computing)#Models). Dann wird ein Modell zum Erwerben und Freigeben von Sperren für `nextidx` benötigt, da es nicht sicher ist, mehreren Prozessen zu erlauben, gleichzeitig auf eine Ressource zuzugreifen.

## [Code Availability and Loading Packages](@id code-availability)

Ihr Code muss in jedem Prozess verfügbar sein, der ihn ausführt. Geben Sie beispielsweise Folgendes an der Julia-Eingabeaufforderung ein:

```julia-repl
julia> function rand2(dims...)
           return 2*rand(dims...)
       end

julia> rand2(2,2)
2×2 Array{Float64,2}:
 0.153756  0.368514
 1.15119   0.918912

julia> fetch(@spawnat :any rand2(2,2))
ERROR: RemoteException(2, CapturedException(UndefVarError(Symbol("#rand2"))))
Stacktrace:
[...]
```

Prozess 1 kannte die Funktion `rand2`, aber Prozess 2 kannte sie nicht.

Am häufigsten laden Sie Code aus Dateien oder Paketen, und Sie haben eine beträchtliche Flexibilität bei der Steuerung, welche Prozesse Code laden. Betrachten Sie eine Datei, `DummyModule.jl`, die den folgenden Code enthält:

```julia
module DummyModule

export MyType, f

mutable struct MyType
    a::Int
end

f(x) = x^2+1

println("loaded")

end
```

Um `MyType` in allen Prozessen zu referenzieren, muss `DummyModule.jl` in jedem Prozess geladen werden. Der Aufruf von `include("DummyModule.jl")` lädt es nur in einem einzelnen Prozess. Um es in jedem Prozess zu laden, verwenden Sie das [`@everywhere`](@ref) Makro (starten Sie Julia mit `julia -p 2`):

```julia-repl
julia> @everywhere include("DummyModule.jl")
loaded
      From worker 3:    loaded
      From worker 2:    loaded
```

Wie gewohnt bringt dies `DummyModule` in keinem der Prozesse in den Geltungsbereich, was [`using`](@ref) oder [`import`](@ref) erfordert. Darüber hinaus, wenn `DummyModule` in einem Prozess in den Geltungsbereich gebracht wird, ist es in keinem anderen vorhanden:

```julia-repl
julia> using .DummyModule

julia> MyType(7)
MyType(7)

julia> fetch(@spawnat 2 MyType(7))
ERROR: On worker 2:
UndefVarError: `MyType` not defined in `Main`
⋮

julia> fetch(@spawnat 2 DummyModule.MyType(7))
MyType(7)
```

Es ist jedoch weiterhin möglich, beispielsweise einen `MyType` an einen Prozess zu senden, der `DummyModule` geladen hat, auch wenn es nicht im Geltungsbereich ist:

```julia-repl
julia> put!(RemoteChannel(2), MyType(7))
RemoteChannel{Channel{Any}}(2, 1, 13)
```

Eine Datei kann auch beim Start in mehreren Prozessen mit dem `-L`-Flag vorab geladen werden, und ein Treiberskript kann verwendet werden, um die Berechnung zu steuern:

```
julia -p <n> -L file1.jl -L file2.jl driver.jl
```

Der Julia-Prozess, der das Treiberskript im obigen Beispiel ausführt, hat eine `id`, die gleich 1 ist, genau wie ein Prozess, der eine interaktive Eingabeaufforderung bereitstellt.

Schließlich, wenn `DummyModule.jl` keine eigenständige Datei, sondern ein Paket ist, dann wird `using DummyModule` `DummyModule.jl` in allen Prozessen *laden*, bringt es jedoch nur in den Geltungsbereich des Prozesses, in dem [`using`](@ref) aufgerufen wurde.

## Starting and managing worker processes

Die Basisinstallation von Julia bietet integrierte Unterstützung für zwei Arten von Clustern:

  * Ein lokaler Cluster, der mit der `-p` Option wie oben gezeigt angegeben ist.
  * Ein Cluster, der Maschinen mit der Option `--machine-file` spannt. Dies verwendet eine passwortlose `ssh`-Anmeldung, um Julia-Arbeitsprozesse (aus demselben Verzeichnis wie der aktuelle Host) auf den angegebenen Maschinen zu starten. Jede Maschinenbeschreibung hat die Form `[count*][user@]host[:port] [bind_addr[:port]]`. `user` ist standardmäßig der aktuelle Benutzer, `port` der Standard-ssh-Port. `count` ist die Anzahl der zu startenden Arbeitsprozesse auf dem Knoten und hat standardmäßig den Wert 1. Die optionale `bind-to bind_addr[:port]` gibt die IP-Adresse und den Port an, die andere Arbeitsprozesse verwenden sollten, um sich mit diesem Arbeitsprozess zu verbinden.

!!! note
    Während Julia im Allgemeinen nach Rückwärtskompatibilität strebt, beruht die Verteilung von Code an Arbeitsprozesse auf [`Serialization.serialize`](@ref). Wie in der entsprechenden Dokumentation hervorgehoben, kann dies nicht garantiert werden, um über verschiedene Julia-Versionen hinweg zu funktionieren, daher wird empfohlen, dass alle Arbeiter auf allen Maschinen dieselbe Version verwenden.


Funktionen [`addprocs`](@ref), [`rmprocs`](@ref), [`workers`](@ref) und andere stehen als programmatische Mittel zur Verfügung, um Prozesse in einem Cluster hinzuzufügen, zu entfernen und abzufragen.

```julia-repl
julia> using Distributed

julia> addprocs(2)
2-element Array{Int64,1}:
 2
 3
```

Modul [`Distributed`](@ref man-distributed) muss explizit im Master-Prozess geladen werden, bevor [`addprocs`](@ref) aufgerufen wird. Es ist automatisch in den Arbeitsprozessen verfügbar.

!!! note
    Beachten Sie, dass Arbeiter kein `~/.julia/config/startup.jl`-Startskript ausführen und ihren globalen Zustand (wie Befehlszeilenoptionen, globale Variablen, neue Methodendefinitionen und geladene Module) nicht mit anderen laufenden Prozessen synchronisieren. Sie können `addprocs(exeflags="--project")` verwenden, um einen Arbeiter mit einer bestimmten Umgebung zu initialisieren, und dann `@everywhere using <modulename>` oder `@everywhere include("file.jl")`.


Andere Arten von Clustern können unterstützt werden, indem Sie Ihren eigenen benutzerdefinierten `ClusterManager` schreiben, wie im Abschnitt [ClusterManagers](@ref) beschrieben.

## Data Movement

Das Senden von Nachrichten und das Bewegen von Daten stellen den Großteil des Overheads in einem verteilten Programm dar. Die Reduzierung der Anzahl der Nachrichten und der Menge der gesendeten Daten ist entscheidend für die Erreichung von Leistung und Skalierbarkeit. Zu diesem Zweck ist es wichtig, die Datenbewegung zu verstehen, die durch Julias verschiedene Konstrukte für verteiltes Programmieren durchgeführt wird.

[`fetch`](@ref) kann als eine explizite Datenbewegungsoperation betrachtet werden, da sie direkt verlangt, dass ein Objekt auf die lokale Maschine verschoben wird. [`@spawnat`](@ref) (und einige verwandte Konstrukte) bewegen ebenfalls Daten, aber dies ist nicht so offensichtlich, daher kann es als eine implizite Datenbewegungsoperation bezeichnet werden. Betrachten Sie diese beiden Ansätze zum Konstruieren und Quadrieren einer zufälligen Matrix:

Methode 1:

```julia-repl
julia> A = rand(1000,1000);

julia> Bref = @spawnat :any A^2;

[...]

julia> fetch(Bref);
```

Methode 2:

```julia-repl
julia> Bref = @spawnat :any rand(1000,1000)^2;

[...]

julia> fetch(Bref);
```

Der Unterschied scheint trivial zu sein, ist aber in der Tat ziemlich signifikant aufgrund des Verhaltens von [`@spawnat`](@ref). Im ersten Verfahren wird eine Zufallsmatrix lokal erstellt und dann an einen anderen Prozess gesendet, wo sie quadriert wird. Im zweiten Verfahren wird eine Zufallsmatrix sowohl erstellt als auch auf einem anderen Prozess quadriert. Daher sendet das zweite Verfahren viel weniger Daten als das erste.

In diesem Spielzeugbeispiel sind die beiden Methoden leicht zu unterscheiden und auszuwählen. In einem echten Programm könnte das Entwerfen der Datenbewegung jedoch mehr Überlegung und wahrscheinlich einige Messungen erfordern. Wenn beispielsweise der erste Prozess die Matrix `A` benötigt, könnte die erste Methode besser sein. Oder wenn das Berechnen von `A` teuer ist und nur der aktuelle Prozess sie hat, könnte es unvermeidlich sein, sie zu einem anderen Prozess zu verschieben. Oder wenn der aktuelle Prozess zwischen dem [`@spawnat`](@ref) und `fetch(Bref)` sehr wenig zu tun hat, könnte es besser sein, den Parallelismus ganz zu eliminieren. Oder stellen Sie sich vor, `rand(1000,1000)` wird durch eine teurere Operation ersetzt. Dann könnte es sinnvoll sein, eine weitere `4d61726b646f776e2e436f64652822222c202240737061776e61742229_40726566`-Anweisung nur für diesen Schritt hinzuzufügen.

## Global variables

Ausdrücke, die remote über [`@spawnat`](@ref) ausgeführt werden, oder Closures, die für die remote Ausführung unter Verwendung von [`remotecall`](@ref) angegeben sind, können auf globale Variablen verweisen. Globale Bindungen im Modul `Main` werden etwas anders behandelt als globale Bindungen in anderen Modulen. Betrachten Sie den folgenden Codeausschnitt:

```julia-repl
A = rand(10,10)
remotecall_fetch(()->sum(A), 2)
```

In diesem Fall muss [`sum`](@ref) im Remote-Prozess definiert sein. Beachten Sie, dass `A` eine globale Variable ist, die im lokalen Arbeitsbereich definiert ist. Arbeiter 2 hat keine Variable namens `A` unter `Main`. Der Akt, den Closure `()->sum(A)` zu Arbeiter 2 zu versenden, führt dazu, dass `Main.A` auf 2 definiert wird. `Main.A` bleibt auf Arbeiter 2 bestehen, selbst nachdem der Aufruf [`remotecall_fetch`](@ref) zurückkehrt. Remote-Aufrufe mit eingebetteten globalen Referenzen (nur unter dem `Main`-Modul) verwalten Globals wie folgt:

  * Neue globale Bindungen werden auf Zielarbeitern erstellt, wenn sie als Teil eines Remoteaufrufs referenziert werden.
  * Globale Konstanten werden auch auf entfernten Knoten als Konstanten deklariert.
  * Globals werden nur im Kontext eines Remote-Calls an einen Ziel-Worker erneut gesendet, und dann nur, wenn sich ihr Wert geändert hat. Außerdem synchronisiert der Cluster keine globalen Bindungen zwischen den Knoten. Zum Beispiel:

    ```julia
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 2) # worker 2
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 3) # worker 3
    A = nothing
    ```

    Die Ausführung des obigen Snippets führt dazu, dass `Main.A` auf Worker 2 einen anderen Wert hat als `Main.A` auf Worker 3, während der Wert von `Main.A` auf Knoten 1 auf `nothing` gesetzt ist.

Wie Sie vielleicht bemerkt haben, kann der mit Globals verbundene Speicher gesammelt werden, wenn sie auf dem Master neu zugewiesen werden, jedoch wird auf den Arbeitern keine solche Aktion durchgeführt, da die Bindungen weiterhin gültig sind. [`clear!`](@ref) kann verwendet werden, um spezifische Globals auf entfernten Knoten manuell auf `nothing` neu zuzuweisen, sobald sie nicht mehr benötigt werden. Dies wird den mit ihnen verbundenen Speicher im Rahmen eines regulären Garbage-Collection-Zyklus freigeben.

Daher sollten Programme vorsichtig sein, wenn sie globale Variablen in Remote-Aufrufen referenzieren. Tatsächlich ist es vorzuziehen, sie ganz zu vermeiden, wenn möglich. Wenn Sie globale Variablen referenzieren müssen, ziehen Sie in Betracht, `let`-Blöcke zu verwenden, um globale Variablen zu lokalisieren.

Zum Beispiel:

```julia-repl
julia> A = rand(10,10);

julia> remotecall_fetch(()->A, 2);

julia> B = rand(10,10);

julia> let B = B
           remotecall_fetch(()->B, 2)
       end;

julia> @fetchfrom 2 InteractiveUtils.varinfo()
name           size summary
––––––––– ––––––––– ––––––––––––––––––––––
A         800 bytes 10×10 Array{Float64,2}
Base                Module
Core                Module
Main                Module
```

Wie zu sehen ist, wird die globale Variable `A` auf Arbeiter 2 definiert, aber `B` wird als lokale Variable erfasst und daher existiert keine Bindung für `B` auf Arbeiter 2.

## Parallel Map and Loops

Glücklicherweise erfordern viele nützliche parallele Berechnungen keine Datenbewegung. Ein häufiges Beispiel ist eine Monte-Carlo-Simulation, bei der mehrere Prozesse unabhängig voneinander Simulationsversuche gleichzeitig durchführen können. Wir können [`@spawnat`](@ref) verwenden, um Münzen auf zwei Prozessen zu werfen. Zuerst schreiben Sie die folgende Funktion in `count_heads.jl`:

```julia
function count_heads(n)
    c::Int = 0
    for i = 1:n
        c += rand(Bool)
    end
    c
end
```

Die Funktion `count_heads` addiert einfach `n` zufällige Bits zusammen. Hier ist, wie wir einige Versuche auf zwei Maschinen durchführen und die Ergebnisse zusammenfassen können:

```julia-repl
julia> @everywhere include_string(Main, $(read("count_heads.jl", String)), "count_heads.jl")

julia> a = @spawnat :any count_heads(100000000)
Future(2, 1, 6, nothing)

julia> b = @spawnat :any count_heads(100000000)
Future(3, 1, 7, nothing)

julia> fetch(a)+fetch(b)
100001564
```

Dieses Beispiel demonstriert ein leistungsstarkes und häufig verwendetes Muster der parallelen Programmierung. Viele Iterationen laufen unabhängig über mehrere Prozesse, und dann werden ihre Ergebnisse mit einer Funktion kombiniert. Der Kombinationsprozess wird als *Reduktion* bezeichnet, da er im Allgemeinen die Tensor-Rang-Reduktion durchführt: Ein Vektor von Zahlen wird auf eine einzelne Zahl reduziert, oder eine Matrix wird auf eine einzelne Zeile oder Spalte reduziert usw. Im Code sieht dies typischerweise wie das Muster `x = f(x,v[i])` aus, wobei `x` der Akkumulator ist, `f` die Reduktionsfunktion ist und die `v[i]` die Elemente sind, die reduziert werden. Es ist wünschenswert, dass `f` assoziativ ist, damit es keine Rolle spielt, in welcher Reihenfolge die Operationen ausgeführt werden.

Beachten Sie, dass unsere Verwendung dieses Musters mit `count_heads` verallgemeinert werden kann. Wir haben zwei explizite [`@spawnat`](@ref)-Anweisungen verwendet, was die Parallelität auf zwei Prozesse beschränkt. Um auf beliebig vielen Prozessen zu arbeiten, können wir eine *parallele Schleife* verwenden, die im verteilten Speicher läuft und in Julia mit [`@distributed`](@ref) wie folgt geschrieben werden kann:

```julia
nheads = @distributed (+) for i = 1:200000000
    Int(rand(Bool))
end
```

Dieser Konstrukt implementiert das Muster, Iterationen mehreren Prozessen zuzuweisen und sie mit einer angegebenen Reduktion (in diesem Fall `(+)`) zu kombinieren. Das Ergebnis jeder Iteration wird als Wert des letzten Ausdrucks innerhalb der Schleife genommen. Der gesamte parallele Schleifenausdruck selbst bewertet sich zum endgültigen Ergebnis.

Beachten Sie, dass obwohl parallele for-Schleifen wie serielle for-Schleifen aussehen, ihr Verhalten dramatisch unterschiedlich ist. Insbesondere finden die Iterationen nicht in einer festgelegten Reihenfolge statt, und Schreibvorgänge in Variablen oder Arrays sind nicht global sichtbar, da die Iterationen auf verschiedenen Prozessen ausgeführt werden. Alle Variablen, die innerhalb der parallelen Schleife verwendet werden, werden kopiert und an jeden Prozess übertragen.

Zum Beispiel wird der folgende Code nicht wie beabsichtigt funktionieren:

```julia
a = zeros(100000)
@distributed for i = 1:100000
    a[i] = i
end
```

Dieser Code wird nicht alle `a` initialisieren, da jeder Prozess eine separate Kopie davon hat. Parallele For-Schleifen wie diese sollten vermieden werden. Glücklicherweise kann [Shared Arrays](@ref man-shared-arrays) verwendet werden, um diese Einschränkung zu umgehen:

```julia
using SharedArrays

a = SharedArray{Float64}(10)
@distributed for i = 1:10
    a[i] = i
end
```

Die Verwendung von "außen" Variablen in parallelen Schleifen ist vollkommen sinnvoll, wenn die Variablen schreibgeschützt sind:

```julia
a = randn(1000)
@distributed (+) for i = 1:100000
    f(a[rand(1:end)])
end
```

Hier wendet jede Iteration `f` auf eine zufällig gewählte Probe aus einem Vektor `a` an, der von allen Prozessen geteilt wird.

Wie Sie sehen können, kann der Reduktionsoperator weggelassen werden, wenn er nicht benötigt wird. In diesem Fall wird die Schleife asynchron ausgeführt, d.h. sie startet unabhängige Aufgaben auf allen verfügbaren Arbeitern und gibt sofort ein Array von [`Future`](@ref Distributed.Future) zurück, ohne auf den Abschluss zu warten. Der Aufrufer kann auf die `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` Abschlüsse zu einem späteren Zeitpunkt warten, indem er [`fetch`](@ref) auf ihnen aufruft, oder auf den Abschluss am Ende der Schleife warten, indem er es mit [`@sync`](@ref) prefixiert, wie `@sync @distributed for`.

In einigen Fällen ist kein Reduktionsoperator erforderlich, und wir möchten lediglich eine Funktion auf alle Ganzzahlen in einem bestimmten Bereich (oder allgemeiner auf alle Elemente in einer Sammlung) anwenden. Dies ist eine weitere nützliche Operation, die als *parallele Abbildung* bezeichnet wird und in Julia als die [`pmap`](@ref)-Funktion implementiert ist. Zum Beispiel könnten wir die singulären Werte mehrerer großer zufälliger Matrizen parallel wie folgt berechnen:

```julia-repl
julia> M = Matrix{Float64}[rand(1000,1000) for i = 1:10];

julia> pmap(svdvals, M);
```

Julias [`pmap`](@ref) ist für den Fall konzipiert, dass jeder Funktionsaufruf eine große Menge an Arbeit verrichtet. Im Gegensatz dazu kann `@distributed for` Situationen handhaben, in denen jede Iteration winzig ist, vielleicht nur das Summieren von zwei Zahlen. Nur Arbeitsprozesse werden sowohl von `4d61726b646f776e2e436f64652822222c2022706d61702229_40726566` als auch von `@distributed for` für die parallele Berechnung verwendet. Im Fall von `@distributed for` erfolgt die endgültige Reduktion im aufrufenden Prozess.

## Remote References and AbstractChannels

Remote-Referenzen beziehen sich immer auf eine Implementierung von `AbstractChannel`.

Eine konkrete Implementierung eines `AbstractChannel` (wie `Channel`) muss [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) und [`wait`](@ref) implementieren. Das entfernte Objekt, auf das durch ein [`Future`](@ref Distributed.Future) verwiesen wird, wird in einem `Channel{Any}(1)` gespeichert, d.h. einem `Channel` der Größe 1, der in der Lage ist, Objekte vom Typ `Any` zu halten.

[`RemoteChannel`](@ref), das umschreibbar ist, kann auf jeden Typ und jede Größe von Kanälen oder jede andere Implementierung eines `AbstractChannel` verweisen.

Der Konstruktor `RemoteChannel(f::Function, pid)()` ermöglicht es uns, Referenzen auf Kanäle zu erstellen, die mehr als einen Wert eines bestimmten Typs halten. `f` ist eine Funktion, die auf `pid` ausgeführt wird und sie muss ein `AbstractChannel` zurückgeben.

Zum Beispiel wird `RemoteChannel(()->Channel{Int}(10), pid)` eine Referenz auf einen Kanal vom Typ `Int` und der Größe 10 zurückgeben. Der Kanal existiert auf dem Worker `pid`.

Methoden [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) und [`wait`](@ref) auf einem [`RemoteChannel`](@ref) werden auf den Backing Store im Remote-Prozess weitergeleitet.

[`RemoteChannel`](@ref) kann somit verwendet werden, um benutzerimplementierte `AbstractChannel`-Objekte zu referenzieren. Ein einfaches Beispiel dafür ist der folgende `DictChannel`, der ein Wörterbuch als seinen entfernten Speicher verwendet:

```jldoctest
julia> struct DictChannel{T} <: AbstractChannel{T}
           d::Dict
           cond_take::Threads.Condition    # waiting for data to become available
           DictChannel{T}() where {T} = new(Dict(), Threads.Condition())
           DictChannel() = DictChannel{Any}()
       end

julia> begin
       function Base.put!(D::DictChannel, k, v)
           @lock D.cond_take begin
               D.d[k] = v
               notify(D.cond_take)
           end
           return D
       end
       function Base.take!(D::DictChannel, k)
           @lock D.cond_take begin
               v = fetch(D, k)
               delete!(D.d, k)
               return v
           end
       end
       Base.isready(D::DictChannel) = @lock D.cond_take !isempty(D.d)
       Base.isready(D::DictChannel, k) = @lock D.cond_take haskey(D.d, k)
       function Base.fetch(D::DictChannel, k)
           @lock D.cond_take begin
               wait(D, k)
               return D.d[k]
           end
       end
       function Base.wait(D::DictChannel, k)
           @lock D.cond_take begin
               while !isready(D, k)
                   wait(D.cond_take)
               end
           end
       end
       end;

julia> d = DictChannel();

julia> isready(d)
false

julia> put!(d, :k, :v);

julia> isready(d, :k)
true

julia> fetch(d, :k)
:v

julia> wait(d, :k)

julia> take!(d, :k)
:v

julia> isready(d, :k)
false
```

## Channels and RemoteChannels

  * Ein [`Channel`](@ref) ist lokal zu einem Prozess. Arbeiter 2 kann nicht direkt auf ein `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` auf Arbeiter 3 verweisen und umgekehrt. Ein [`RemoteChannel`](@ref) kann jedoch Werte zwischen den Arbeitern setzen und abrufen.
  * Ein [`RemoteChannel`](@ref) kann als ein *Handle* zu einem [`Channel`](@ref) betrachtet werden.
  * Die Prozess-ID, `pid`, die mit einem [`RemoteChannel`](@ref) verbunden ist, identifiziert den Prozess, in dem der Backing Store, d.h. der Backing [`Channel`](@ref), existiert.
  * Jeder Prozess mit einem Verweis auf ein [`RemoteChannel`](@ref) kann Gegenstände aus dem Kanal entnehmen und hineinlegen. Daten werden automatisch an (oder von) dem Prozess gesendet, mit dem ein `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` verbunden ist.
  * Die Serialisierung eines [`Channel`](@ref) serialisiert auch alle Daten, die im Kanal vorhanden sind. Die Deserialisierung macht daher effektiv eine Kopie des ursprünglichen Objekts.
  * Andererseits umfasst die Serialisierung eines [`RemoteChannel`](@ref) nur die Serialisierung eines Identifikators, der den Standort und die Instanz von [`Channel`](@ref) identifiziert, auf die durch den Handle verwiesen wird. Ein deserialisiertes `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566`-Objekt (auf jedem Worker) verweist daher ebenfalls auf denselben Speicher wie das Original.

Das obige Beispiel für Kanäle kann für die Interprozesskommunikation modifiziert werden, wie unten gezeigt.

Wir starten 4 Arbeiter, um einen einzelnen `jobs` Remote-Kanal zu verarbeiten. Jobs, identifiziert durch eine ID (`job_id`), werden in den Kanal geschrieben. Jede remote ausgeführte Aufgabe in dieser Simulation liest eine `job_id`, wartet eine zufällige Zeitspanne und schreibt ein Tupel aus `job_id`, benötigter Zeit und ihrer eigenen `pid` in den Ergebniskanal zurück. Schließlich werden alle `results` im Master-Prozess ausgegeben.

```julia-repl
julia> addprocs(4); # add worker processes

julia> const jobs = RemoteChannel(()->Channel{Int}(32));

julia> const results = RemoteChannel(()->Channel{Tuple}(32));

julia> @everywhere function do_work(jobs, results) # define work function everywhere
           while true
               job_id = take!(jobs)
               exec_time = rand()
               sleep(exec_time) # simulates elapsed time doing actual work
               put!(results, (job_id, exec_time, myid()))
           end
       end

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for p in workers() # start tasks on the workers to process requests in parallel
           remote_do(do_work, p, jobs, results)
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time, where = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds on worker $where")
           global n = n - 1
       end
1 finished in 0.18 seconds on worker 4
2 finished in 0.26 seconds on worker 5
6 finished in 0.12 seconds on worker 4
7 finished in 0.18 seconds on worker 4
5 finished in 0.35 seconds on worker 5
4 finished in 0.68 seconds on worker 2
3 finished in 0.73 seconds on worker 3
11 finished in 0.01 seconds on worker 3
12 finished in 0.02 seconds on worker 3
9 finished in 0.26 seconds on worker 5
8 finished in 0.57 seconds on worker 4
10 finished in 0.58 seconds on worker 2
0.055971741
```

### Remote References and Distributed Garbage Collection

Objekte, auf die durch entfernte Referenzen verwiesen wird, können nur freigegeben werden, wenn *alle* gehaltenen Referenzen im Cluster gelöscht sind.

Der Knoten, in dem der Wert gespeichert ist, verfolgt, welche der Arbeiter eine Referenz darauf haben. Jedes Mal, wenn ein [`RemoteChannel`](@ref) oder ein (nicht abgerufenes) [`Future`](@ref Distributed.Future) an einen Arbeiter serialisiert wird, wird der Knoten, auf den die Referenz zeigt, benachrichtigt. Und jedes Mal, wenn ein `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` oder ein (nicht abgerufenes) `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` lokal als nicht mehr benötigt gesammelt wird, wird der Knoten, der den Wert besitzt, erneut benachrichtigt. Dies ist in einem internen, clusterbewussten Serializer implementiert. Remote-Referenzen sind nur im Kontext eines laufenden Clusters gültig. Das Serialisieren und Deserialisieren von Referenzen zu und von regulären `IO`-Objekten wird nicht unterstützt.

Die Benachrichtigungen erfolgen durch das Senden von "Tracking"-Nachrichten – eine "Referenz hinzufügen"-Nachricht, wenn eine Referenz in einen anderen Prozess serialisiert wird, und eine "Referenz löschen"-Nachricht, wenn eine Referenz lokal garbage collected wird.

Da [`Future`](@ref Distributed.Future) einmal geschrieben und lokal zwischengespeichert werden, aktualisiert der Akt des [`fetch`](@ref) eines `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` auch die Referenzverfolgungsinformationen auf dem Knoten, der den Wert besitzt.

Der Knoten, der den Wert besitzt, gibt ihn frei, sobald alle Verweise darauf gelöscht sind.

Mit [`Future`](@ref Distributed.Future) wird das Serialisieren eines bereits abgerufenen `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` an einen anderen Knoten ebenfalls den Wert gesendet, da der ursprüngliche Remote-Speicher den Wert bis zu diesem Zeitpunkt möglicherweise gesammelt hat.

Es ist wichtig zu beachten, dass *wann* ein Objekt lokal garbage collected wird, von der Größe des Objekts und dem aktuellen Speicherbedarf im System abhängt.

Im Falle von Remote-Referenzen ist die Größe des lokalen Referenzobjekts recht klein, während der auf dem Remote-Knoten gespeicherte Wert recht groß sein kann. Da das lokale Objekt möglicherweise nicht sofort gesammelt wird, ist es eine gute Praxis, [`finalize`](@ref) auf lokalen Instanzen eines [`RemoteChannel`](@ref) oder auf nicht abgerufenen [`Future`](@ref Distributed.Future)s explizit aufzurufen. Da das Aufrufen von [`fetch`](@ref) auf einem `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` auch seine Referenz aus dem Remote-Speicher entfernt, ist dies bei abgerufenen `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`s nicht erforderlich. Das explizite Aufrufen von `4d61726b646f776e2e436f64652822222c202266696e616c697a652229_40726566` führt zu einer sofortigen Nachricht, die an den Remote-Knoten gesendet wird, um fortzufahren und seine Referenz auf den Wert zu entfernen.

Sobald sie finalisiert ist, wird eine Referenz ungültig und kann in weiteren Aufrufen nicht mehr verwendet werden.

## Local invocations

Daten werden notwendigerweise zum Remote-Knoten für die Ausführung kopiert. Dies gilt sowohl für Remotecalls als auch wenn Daten in eine [`RemoteChannel`](@ref) / [`Future`](@ref Distributed.Future) auf einem anderen Knoten gespeichert werden. Wie erwartet führt dies zu einer Kopie der serialisierten Objekte auf dem Remote-Knoten. Wenn jedoch der Zielknoten der lokale Knoten ist, d.h. die Prozess-ID des Aufrufers die gleiche ist wie die ID des Remote-Knotens, wird er als lokaler Aufruf ausgeführt. Er wird normalerweise (nicht immer) in einer anderen Aufgabe ausgeführt - aber es gibt keine Serialisierung/Deserialisierung von Daten. Folglich verweist der Aufruf auf die gleichen Objektinstanzen wie übergeben - es werden keine Kopien erstellt. Dieses Verhalten wird unten hervorgehoben:

```julia-repl
julia> using Distributed;

julia> rc = RemoteChannel(()->Channel(3));   # RemoteChannel created on local node

julia> v = [0];

julia> for i in 1:3
           v[1] = i                          # Reusing `v`
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[3], [3], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 1

julia> addprocs(1);

julia> rc = RemoteChannel(()->Channel(3), workers()[1]);   # RemoteChannel created on remote node

julia> v = [0];

julia> for i in 1:3
           v[1] = i
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[1], [2], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 3
```

Wie zu sehen ist, [`put!`](@ref) auf einem lokal besessenen [`RemoteChannel`](@ref) mit dem gleichen Objekt `v`, das zwischen den Aufrufen modifiziert wird, führt zu derselben einzelnen Objektinstanz, die gespeichert wird. Im Gegensatz dazu werden Kopien von `v` erstellt, wenn der Knoten, der `rc` besitzt, ein anderer Knoten ist.

Es ist zu beachten, dass dies im Allgemeinen kein Problem darstellt. Es ist nur dann zu berücksichtigen, wenn das Objekt sowohl lokal gespeichert als auch nach dem Aufruf modifiziert wird. In solchen Fällen kann es angemessen sein, eine `deepcopy` des Objekts zu speichern.

Dies gilt auch für Remotecalls auf dem lokalen Knoten, wie im folgenden Beispiel zu sehen ist:

```julia-repl
julia> using Distributed; addprocs(1);

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), myid(), v);     # Executed on local node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[1], v2=[1], true

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), workers()[1], v); # Executed on remote node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[0], v2=[1], false
```

Wie man erneut sehen kann, verhält sich ein Remote-Aufruf auf den lokalen Knoten genau wie ein direkter Aufruf. Der Aufruf ändert lokale Objekte, die als Argumente übergeben werden. Bei der Remote-Aufruf wird auf einer Kopie der Argumente gearbeitet.

Um es zu wiederholen, im Allgemeinen ist dies kein Problem. Wenn der lokale Knoten auch als Rechenknoten verwendet wird und die Argumente nach dem Aufruf verwendet werden, muss dieses Verhalten berücksichtigt werden, und falls erforderlich, müssen tiefe Kopien der Argumente an den Aufruf übergeben werden, der auf dem lokalen Knoten aufgerufen wird. Aufrufe auf entfernten Knoten arbeiten immer mit Kopien der Argumente.

## [Shared Arrays](@id man-shared-arrays)

Geteilte Arrays verwenden den systemeigenen gemeinsamen Speicher, um dasselbe Array über viele Prozesse hinweg abzubilden. Ein [`SharedArray`](@ref) ist eine gute Wahl, wenn Sie eine große Menge an Daten haben möchten, die von zwei oder mehr Prozessen auf demselben Rechner gemeinsam zugänglich sind. Die Unterstützung für Geteilte Arrays ist über das Modul `SharedArrays` verfügbar, das auf allen beteiligten Arbeitern explizit geladen werden muss.

Eine komplementäre Datenstruktur wird durch das externe Paket [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) in Form eines `DArray` bereitgestellt. Während es einige Ähnlichkeiten zu einem [`SharedArray`](@ref) gibt, ist das Verhalten eines [`DArray`](https://github.com/JuliaParallel/DistributedArrays.jl) ganz anders. In einem `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` hat jeder "teilnehmende" Prozess Zugriff auf das gesamte Array; im Gegensatz dazu hat in einem `4d61726b646f776e2e436f64652822222c20224441727261792229_68747470733a2f2f6769746875622e636f6d2f4a756c6961506172616c6c656c2f44697374726962757465644172726179732e6a6c` jeder Prozess nur lokalen Zugriff auf einen Teil der Daten, und keine zwei Prozesse teilen sich denselben Teil.

[`SharedArray`](@ref) Indizierung (Zuweisung und Zugriff auf Werte) funktioniert genau wie bei regulären Arrays und ist effizient, da der zugrunde liegende Speicher dem lokalen Prozess zur Verfügung steht. Daher funktionieren die meisten Algorithmen ganz natürlich mit `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`, wenn auch im Einzelprozessmodus. In Fällen, in denen ein Algorithmus auf eine [`Array`](@ref)-Eingabe besteht, kann das zugrunde liegende Array von einem `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` abgerufen werden, indem [`sdata`](@ref) aufgerufen wird. Für andere `AbstractArray`-Typen gibt `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` einfach das Objekt selbst zurück, sodass es sicher ist, `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` auf jedem `Array`-Typ-Objekt zu verwenden.

Der Konstruktor für ein gemeinsames Array hat die Form:

```julia
SharedArray{T,N}(dims::NTuple; init=false, pids=Int[])
```

welches ein `N`-dimensionales gemeinsames Array eines Bits vom Typ `T` und der Größe `dims` über die durch `pids` angegebenen Prozesse erstellt. Im Gegensatz zu verteilten Arrays ist ein gemeinsames Array nur von den an den angegebenen Arbeitern teilnehmenden Prozessen zugänglich (und auch vom erstellenden Prozess, wenn er sich auf demselben Host befindet). Beachten Sie, dass nur Elemente, die [`isbits`](@ref) sind, in einem SharedArray unterstützt werden.

Wenn eine `init`-Funktion mit der Signatur `initfn(S::SharedArray)` angegeben ist, wird sie auf allen beteiligten Arbeitern aufgerufen. Sie können angeben, dass jeder Arbeiter die `init`-Funktion auf einem bestimmten Teil des Arrays ausführt, wodurch die Initialisierung parallelisiert wird.

Hier ist ein kurzes Beispiel:

```julia-repl
julia> using Distributed

julia> addprocs(3)
3-element Array{Int64,1}:
 2
 3
 4

julia> @everywhere using SharedArrays

julia> S = SharedArray{Int,2}((3,4), init = S -> S[localindices(S)] = repeat([myid()], length(localindices(S))))
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  3  4  4

julia> S[3,2] = 7
7

julia> S
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  7  4  4
```

[`SharedArrays.localindices`](@ref) bietet disjunkte eindimensionale Bereiche von Indizes und ist manchmal praktisch, um Aufgaben unter Prozessen aufzuteilen. Sie können die Arbeit natürlich auf jede gewünschte Weise aufteilen:

```julia-repl
julia> S = SharedArray{Int,2}((3,4), init = S -> S[indexpids(S):length(procs(S)):length(S)] = repeat([myid()], length( indexpids(S):length(procs(S)):length(S))))
3×4 SharedArray{Int64,2}:
 2  2  2  2
 3  3  3  3
 4  4  4  4
```

Da alle Prozesse Zugriff auf die zugrunde liegenden Daten haben, müssen Sie darauf achten, keine Konflikte zu verursachen. Zum Beispiel:

```julia
@sync begin
    for p in procs(S)
        @async begin
            remotecall_wait(fill!, p, S, p)
        end
    end
end
```

würde zu undefiniertem Verhalten führen. Da jeder Prozess das *gesamte* Array mit seiner eigenen `pid` füllt, wird die `pid` des Prozesses, der als letzter ausgeführt wird (für ein bestimmtes Element von `S`), beibehalten.

Als ein erweitertes und komplexeres Beispiel, ziehen Sie in Betracht, den folgenden "Kernel" parallel auszuführen:

```julia
q[i,j,t+1] = q[i,j,t] + u[i,j,t]
```

In diesem Fall, wenn wir versuchen, die Arbeit mit einem eindimensionalen Index aufzuteilen, werden wir wahrscheinlich auf Probleme stoßen: Wenn `q[i,j,t]` am Ende des Blocks ist, der einem Arbeiter zugewiesen ist, und `q[i,j,t+1]` am Anfang des Blocks ist, der einem anderen zugewiesen ist, ist es sehr wahrscheinlich, dass `q[i,j,t]` nicht bereit ist, wenn es für die Berechnung von `q[i,j,t+1]` benötigt wird. In solchen Fällen ist es besser, das Array manuell zu chunkieren. Lassen Sie uns entlang der zweiten Dimension aufteilen. Definieren Sie eine Funktion, die die `(irange, jrange)` Indizes zurückgibt, die diesem Arbeiter zugewiesen sind:

```julia-repl
julia> @everywhere function myrange(q::SharedArray)
           idx = indexpids(q)
           if idx == 0 # This worker is not assigned a piece
               return 1:0, 1:0
           end
           nchunks = length(procs(q))
           splits = [round(Int, s) for s in range(0, stop=size(q,2), length=nchunks+1)]
           1:size(q,1), splits[idx]+1:splits[idx+1]
       end
```

Als Nächstes definieren Sie den Kernel:

```julia-repl
julia> @everywhere function advection_chunk!(q, u, irange, jrange, trange)
           @show (irange, jrange, trange)  # display so we can see what's happening
           for t in trange, j in jrange, i in irange
               q[i,j,t+1] = q[i,j,t] + u[i,j,t]
           end
           q
       end
```

Wir definieren auch einen praktischen Wrapper für eine `SharedArray`-Implementierung.

```julia-repl
julia> @everywhere advection_shared_chunk!(q, u) =
           advection_chunk!(q, u, myrange(q)..., 1:size(q,3)-1)
```

Jetzt vergleichen wir drei verschiedene Versionen, von denen eine in einem einzelnen Prozess läuft:

```julia-repl
julia> advection_serial!(q, u) = advection_chunk!(q, u, 1:size(q,1), 1:size(q,2), 1:size(q,3)-1);
```

einer, der [`@distributed`](@ref) verwendet:

```julia-repl
julia> function advection_parallel!(q, u)
           for t = 1:size(q,3)-1
               @sync @distributed for j = 1:size(q,2)
                   for i = 1:size(q,1)
                       q[i,j,t+1]= q[i,j,t] + u[i,j,t]
                   end
               end
           end
           q
       end;
```

und einer, der in Teilen delegiert:

```julia-repl
julia> function advection_shared!(q, u)
           @sync begin
               for p in procs(q)
                   @async remotecall_wait(advection_shared_chunk!, p, q, u)
               end
           end
           q
       end;
```

Wenn wir `SharedArray`s erstellen und diese Funktionen zeitlich messen, erhalten wir die folgenden Ergebnisse (mit `julia -p 4`):

```julia-repl
julia> q = SharedArray{Float64,3}((500,500,500));

julia> u = SharedArray{Float64,3}((500,500,500));
```

Führen Sie die Funktionen einmal aus, um sie JIT-zu kompilieren und [`@time`](@ref) sie beim zweiten Durchlauf auszuführen:

```julia-repl
julia> @time advection_serial!(q, u);
(irange,jrange,trange) = (1:500,1:500,1:499)
 830.220 milliseconds (216 allocations: 13820 bytes)

julia> @time advection_parallel!(q, u);
   2.495 seconds      (3999 k allocations: 289 MB, 2.09% gc time)

julia> @time advection_shared!(q,u);
        From worker 2:       (irange,jrange,trange) = (1:500,1:125,1:499)
        From worker 4:       (irange,jrange,trange) = (1:500,251:375,1:499)
        From worker 3:       (irange,jrange,trange) = (1:500,126:250,1:499)
        From worker 5:       (irange,jrange,trange) = (1:500,376:500,1:499)
 238.119 milliseconds (2264 allocations: 169 KB)
```

Der größte Vorteil von `advection_shared!` besteht darin, dass der Datenverkehr zwischen den Arbeitern minimiert wird, sodass jeder für längere Zeit an dem zugewiesenen Teil rechnen kann.

### Shared Arrays and Distributed Garbage Collection

Wie entfernte Referenzen sind auch gemeinsame Arrays von der Garbage Collection des erstellenden Knotens abhängig, um Referenzen von allen beteiligten Arbeitern freizugeben. Code, der viele kurzlebige gemeinsame Array-Objekte erstellt, würde davon profitieren, diese Objekte so schnell wie möglich explizit zu finalisieren. Dies führt dazu, dass sowohl der Speicher als auch die Dateihandles, die das gemeinsame Segment abbilden, früher freigegeben werden.

## ClusterManagers

Das Starten, Verwalten und Vernetzen von Julia-Prozessen in einem logischen Cluster erfolgt über Cluster-Manager. Ein `ClusterManager` ist verantwortlich für

  * Starten von Arbeitsprozessen in einer Clusterumgebung
  * Verwaltung von Ereignissen während der Lebensdauer jedes Arbeiters
  * optional, Datenübertragung bereitstellen

Ein Julia-Cluster hat die folgenden Eigenschaften:

  * Der ursprüngliche Julia-Prozess, auch als `master` bezeichnet, ist besonders und hat eine `id` von 1.
  * Nur der `master`-Prozess kann Arbeitsprozesse hinzufügen oder entfernen.
  * Alle Prozesse können direkt miteinander kommunizieren.

Verbindungen zwischen Arbeitern (unter Verwendung des integrierten TCP/IP-Transports) werden auf folgende Weise hergestellt:

  * [`addprocs`](@ref) wird im Masterprozess mit einem `ClusterManager`-Objekt aufgerufen.
  * [`addprocs`](@ref) ruft die entsprechende [`launch`](@ref) Methode auf, die die erforderliche Anzahl von Arbeitsprozessen auf den entsprechenden Maschinen startet.
  * Jeder Arbeiter beginnt, auf einem freien Port zu lauschen und gibt seine Host- und Portinformationen in [`stdout`](@ref) aus.
  * Der Cluster-Manager erfasst den [`stdout`](@ref) jedes Arbeiters und stellt ihn dem Master-Prozess zur Verfügung.
  * Der Master-Prozess analysiert diese Informationen und richtet TCP/IP-Verbindungen zu jedem Worker ein.
  * Jeder Arbeiter wird auch über andere Arbeiter im Cluster informiert.
  * Jeder Arbeiter verbindet sich mit allen Arbeitern, deren `id` kleiner ist als die eigene `id`.
  * Auf diese Weise wird ein Mesh-Netzwerk eingerichtet, in dem jeder Arbeiter direkt mit jedem anderen Arbeiter verbunden ist.

Während die Standard-Transportschicht [`TCPSocket`](@ref) verwendet, ist es möglich, dass ein Julia-Cluster seinen eigenen Transport bereitstellt.

Julia bietet zwei integrierte Cluster-Manager:

  * `LocalManager`, verwendet, wenn [`addprocs()`](@ref) oder [`addprocs(np::Integer)`](@ref) aufgerufen werden.
  * `SSHManager`, verwendet, wenn [`addprocs(hostnames::Array)`](@ref) mit einer Liste von Hostnamen aufgerufen wird.

`LocalManager` wird verwendet, um zusätzliche Arbeiter auf demselben Host zu starten, wodurch die Hardware mit mehreren Kernen und mehreren Prozessoren genutzt wird.

Daher müsste ein minimaler Cluster-Manager Folgendes tun:

  * sein ein Subtyp des abstrakten `ClusterManager`
  * implement [`launch`](@ref), eine Methode, die für das Starten neuer Arbeiter verantwortlich ist.
  * implement [`manage`](@ref), die bei verschiedenen Ereignissen während der Lebensdauer eines Arbeiters aufgerufen wird (zum Beispiel beim Senden eines Interruptsignals)

[`addprocs(manager::FooManager)`](@ref addprocs) erfordert, dass `FooManager` implementiert:

```julia
function launch(manager::FooManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

Als Beispiel sehen wir uns an, wie der `LocalManager`, der Manager, der dafür verantwortlich ist, Arbeiter auf demselben Host zu starten, implementiert ist:

```julia
struct LocalManager <: ClusterManager
    np::Integer
end

function launch(manager::LocalManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::LocalManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

Die [`launch`](@ref)-Methode nimmt die folgenden Argumente:

  * `manager::ClusterManager`: der Cluster-Manager, mit dem [`addprocs`](@ref) aufgerufen wird.
  * `params::Dict`: alle Schlüsselwortargumente, die an [`addprocs`](@ref) übergeben wurden.
  * `launched::Array`: das Array, dem ein oder mehrere `WorkerConfig`-Objekte hinzugefügt werden sollen
  * `c::Condition`: die Bedingungsvariable, die benachrichtigt wird, wenn Arbeiter gestartet werden

Die [`launch`](@ref)-Methode wird asynchron in einer separaten Aufgabe aufgerufen. Die Beendigung dieser Aufgabe signalisiert, dass alle angeforderten Arbeiter gestartet wurden. Daher muss die `4d61726b646f776e2e436f64652822222c20226c61756e63682229_40726566`-Funktion SOFORT beendet werden, sobald alle angeforderten Arbeiter gestartet wurden.

Neu gestartete Arbeiter sind miteinander und mit dem Master-Prozess in einer All-zu-Allen-Manier verbunden. Das Angeben des Befehlszeilenarguments `--worker[=<cookie>]` führt dazu, dass die gestarteten Prozesse sich als Arbeiter initialisieren und Verbindungen über TCP/IP-Sockets eingerichtet werden.

Alle Arbeiter in einem Cluster teilen dasselbe [cookie](@ref man-cluster-cookie) wie der Master. Wenn das Cookie nicht angegeben ist, d.h. mit der `--worker`-Option, versucht der Arbeiter, es von seiner Standardeingabe zu lesen. `LocalManager` und `SSHManager` übergeben das Cookie beiden neu gestarteten Arbeitern über ihre Standardeingaben.

Standardmäßig hört ein Worker auf einem freien Port an der Adresse, die durch einen Aufruf von [`getipaddr()`](@ref) zurückgegeben wird. Eine spezifische Adresse, auf der gehört werden soll, kann durch das optionale Argument `--bind-to bind_addr[:port]` angegeben werden. Dies ist nützlich für multi-homed Hosts.

Als Beispiel für einen Nicht-TCP/IP-Transport kann eine Implementierung wählen, MPI zu verwenden, in diesem Fall darf `--worker` NICHT angegeben werden. Stattdessen sollten neu gestartete Worker `init_worker(cookie)` aufrufen, bevor sie eine der parallelen Konstrukte verwenden.

Für jeden gestarteten Worker muss die Methode [`launch`](@ref) ein `WorkerConfig`-Objekt (mit entsprechend initialisierten Feldern) zu `launched` hinzufügen.

```julia
mutable struct WorkerConfig
    # Common fields relevant to all cluster managers
    io::Union{IO, Nothing}
    host::Union{AbstractString, Nothing}
    port::Union{Integer, Nothing}

    # Used when launching additional workers at a host
    count::Union{Int, Symbol, Nothing}
    exename::Union{AbstractString, Cmd, Nothing}
    exeflags::Union{Cmd, Nothing}

    # External cluster managers can use this to store information at a per-worker level
    # Can be a dict if multiple fields need to be stored.
    userdata::Any

    # SSHManager / SSH tunnel connections to workers
    tunnel::Union{Bool, Nothing}
    bind_addr::Union{AbstractString, Nothing}
    sshflags::Union{Cmd, Nothing}
    max_parallel::Union{Integer, Nothing}

    # Used by Local/SSH managers
    connect_at::Any

    [...]
end
```

Die meisten Felder in `WorkerConfig` werden von den integrierten Managern verwendet. Benutzerdefinierte Cluster-Manager würden typischerweise nur `io` oder `host` / `port` angeben:

  * Wenn `io` angegeben ist, wird es verwendet, um Host-/Portinformationen zu lesen. Ein Julia-Arbeiter gibt beim Start seine Bind-Adresse und den Port aus. Dies ermöglicht es Julia-Arbeitern, auf jedem verfügbaren freien Port zu hören, anstatt dass die Arbeiterports manuell konfiguriert werden müssen.
  * Wenn `io` nicht angegeben ist, werden `host` und `port` verwendet, um eine Verbindung herzustellen.
  * `count`, `exename` und `exeflags` sind relevant für das Starten zusätzlicher Arbeiter von einem Arbeiter aus. Zum Beispiel kann ein Cluster-Manager einen einzelnen Arbeiter pro Knoten starten und diesen verwenden, um zusätzliche Arbeiter zu starten.

      * `count` mit einem ganzzahligen Wert `n` startet insgesamt `n` Arbeiter.
      * `count` mit einem Wert von `:auto` startet so viele Worker, wie es CPU-Threads (logische Kerne) auf diesem Rechner gibt.
      * `exename` ist der Name der `julia`-Ausführungsdatei einschließlich des vollständigen Pfads.
      * `exeflags` sollten auf die erforderlichen Befehlszeilenargumente für neue Arbeiter gesetzt werden.
  * `tunnel`, `bind_addr`, `sshflags` und `max_parallel` werden verwendet, wenn ein SSH-Tunnel erforderlich ist, um von dem Master-Prozess zu den Arbeitern zu verbinden.
  * `userdata` wird bereitgestellt, damit benutzerdefinierte Cluster-Manager ihre eigenen arbeiter-spezifischen Informationen speichern können.

`manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)` wird zu verschiedenen Zeiten während der Lebensdauer des Arbeiters mit geeigneten `op`-Werten aufgerufen:

  * mit `:register`/`:deregister`, wenn ein Worker zum Julia-Worker-Pool hinzugefügt / entfernt wird.
  * mit `:interrupt`, wenn `interrupt(workers)` aufgerufen wird. Der `ClusterManager` sollte den entsprechenden Worker mit einem Interrupt-Signal signalisieren.
  * mit `:finalize` zu Reinigungszwecken.

### Cluster Managers with Custom Transports

Das Ersetzen der standardmäßigen TCP/IP-All-zu-Allen-Socket-Verbindungen durch eine benutzerdefinierte Transportschicht ist etwas komplizierter. Jeder Julia-Prozess hat so viele Kommunikationsaufgaben, wie es Arbeiter gibt, mit denen er verbunden ist. Betrachten wir beispielsweise ein Julia-Cluster mit 32 Prozessen in einem All-zu-Allen-Meschnetzwerk:

  * Jeder Julia-Prozess hat somit 31 Kommunikationsaufgaben.
  * Jede Aufgabe verarbeitet alle eingehenden Nachrichten von einem einzelnen Remote-Mitarbeiter in einer Nachrichtenverarbeitungs-Schleife.
  * Die Nachrichtenverarbeitungs-Schleife wartet auf ein `IO`-Objekt (zum Beispiel ein [`TCPSocket`](@ref) in der Standardimplementierung), liest eine gesamte Nachricht, verarbeitet sie und wartet auf die nächste.
  * Das Senden von Nachrichten an einen Prozess erfolgt direkt von jeder Julia-Aufgabe – nicht nur von Kommunikationstasks – erneut über das entsprechende `IO`-Objekt.

Das Ersetzen des Standardtransports erfordert, dass die neue Implementierung Verbindungen zu entfernten Arbeitern einrichtet und geeignete `IO`-Objekte bereitstellt, auf die die Nachrichtenverarbeitungs-Schleifen warten können. Die spezifischen Rückrufe, die implementiert werden müssen, sind:

```julia
connect(manager::FooManager, pid::Integer, config::WorkerConfig)
kill(manager::FooManager, pid::Int, config::WorkerConfig)
```

Die Standardimplementierung (die TCP/IP-Sockets verwendet) wird als `connect(manager::ClusterManager, pid::Integer, config::WorkerConfig)` implementiert.

`connect` sollte ein Paar von `IO`-Objekten zurückgeben, eines zum Lesen von Daten, die vom Worker `pid` gesendet werden, und das andere zum Schreiben von Daten, die an den Worker `pid` gesendet werden müssen. Benutzerdefinierte Cluster-Manager können einen speicherinternen `BufferStream` als Verbindung verwenden, um Daten zwischen dem benutzerdefinierten, möglicherweise nicht-`IO`-Transport und Julias integrierter paralleler Infrastruktur zu vermitteln.

Ein `BufferStream` ist ein In-Memory [`IOBuffer`](@ref), das sich wie ein `IO` verhält – es ist ein Stream, der asynchron verarbeitet werden kann.

Der Ordner `clustermanager/0mq` in [Examples repository](https://github.com/JuliaAttic/Examples) enthält ein Beispiel für die Verwendung von ZeroMQ, um Julia-Arbeiter in einer Stern-Topologie mit einem 0MQ-Broker in der Mitte zu verbinden. Hinweis: Die Julia-Prozesse sind weiterhin alle *logisch* miteinander verbunden – jeder Arbeiter kann jeden anderen Arbeiter direkt kontaktieren, ohne sich dessen bewusst zu sein, dass 0MQ als Transportebene verwendet wird.

Beim Verwenden von benutzerdefinierten Transporten:

  * Julia-Worker dürfen NICHT mit `--worker` gestartet werden. Das Starten mit `--worker` führt dazu, dass die neu gestarteten Worker standardmäßig die TCP/IP-Socket-Transportimplementierung verwenden.
  * Für jede eingehende logische Verbindung mit einem Worker muss `Base.process_messages(rd::IO, wr::IO)()` aufgerufen werden. Dies startet eine neue Aufgabe, die das Lesen und Schreiben von Nachrichten von/zum Worker, der durch die `IO`-Objekte dargestellt wird, behandelt.
  * `init_worker(cookie, manager::FooManager)` *muss* als Teil der Initialisierung des Arbeitsprozesses aufgerufen werden.
  * Feld `connect_at::Any` in `WorkerConfig` kann vom Cluster-Manager gesetzt werden, wenn [`launch`](@ref) aufgerufen wird. Der Wert dieses Feldes wird in allen [`connect`](@ref) Rückrufen übergeben. Typischerweise enthält es Informationen darüber, *wie man sich* mit einem Worker verbindet. Zum Beispiel verwendet der TCP/IP-Socket-Transport dieses Feld, um das `(host, port)`-Tupel anzugeben, unter dem man sich mit einem Worker verbinden kann.

`kill(manager, pid, config)` wird aufgerufen, um einen Worker aus dem Cluster zu entfernen. Im Master-Prozess müssen die entsprechenden `IO`-Objekte von der Implementierung geschlossen werden, um eine ordnungsgemäße Bereinigung sicherzustellen. Die Standardimplementierung führt einfach einen `exit()`-Aufruf auf dem angegebenen Remote-Worker aus.

Der Beispiele-Ordner `clustermanager/simple` ist ein Beispiel, das eine einfache Implementierung mit UNIX-Domain-Sockets für die Cluster-Einrichtung zeigt.

### Network Requirements for LocalManager and SSHManager

Julia-Cluster sind dafür ausgelegt, in bereits gesicherten Umgebungen auf Infrastrukturen wie lokalen Laptops, Abteilungsclustern oder sogar in der Cloud ausgeführt zu werden. Dieser Abschnitt behandelt die Anforderungen an die Netzwerksicherheit für den integrierten `LocalManager` und `SSHManager`:

  * Der Master-Prozess hört auf keinen Port. Er verbindet sich nur mit den Arbeitern.
  * Jeder Arbeiter bindet sich nur an eine der lokalen Schnittstellen und hört auf einer vom Betriebssystem zugewiesenen ephemeral Portnummer.
  * `LocalManager`, der von `addprocs(N)` verwendet wird, bindet standardmäßig nur an die Loopback-Schnittstelle. Das bedeutet, dass später gestartete Worker auf Remote-Hosts (oder von jemandem mit böswilligen Absichten) nicht in der Lage sind, eine Verbindung zum Cluster herzustellen. Ein `addprocs(4)` gefolgt von einem `addprocs(["remote_host"])` wird fehlschlagen. Einige Benutzer müssen möglicherweise einen Cluster erstellen, der aus ihrem lokalen System und einigen Remote-Systemen besteht. Dies kann erreicht werden, indem man `LocalManager` ausdrücklich anweist, an eine externe Netzwerkschnittstelle über das Schlüsselwort-Argument `restrict` zu binden: `addprocs(4; restrict=false)`.
  * `SSHManager`, verwendet von `addprocs(list_of_remote_hosts)`, startet Worker auf Remote-Hosts über SSH. Standardmäßig wird SSH nur verwendet, um Julia-Worker zu starten. Nachfolgende Master-Worker- und Worker-Worker-Verbindungen verwenden einfache, unverschlüsselte TCP/IP-Sockets. Die Remote-Hosts müssen die passwortlose Anmeldung aktiviert haben. Zusätzliche SSH-Flags oder Anmeldeinformationen können über das Schlüsselwort-Argument `sshflags` angegeben werden.
  * `addprocs(list_of_remote_hosts; tunnel=true, sshflags=<ssh keys and other flags>)` ist nützlich, wenn wir SSH-Verbindungen für Master-Worker ebenfalls verwenden möchten. Ein typisches Szenario dafür ist ein lokales Laptop, das die Julia REPL (d.h. den Master) ausführt, während der Rest des Clusters in der Cloud, sagen wir auf Amazon EC2, läuft. In diesem Fall muss nur Port 22 im Remote-Cluster geöffnet werden, gekoppelt mit einem über die Public Key Infrastructure (PKI) authentifizierten SSH-Client. Authentifizierungsanmeldeinformationen können über `sshflags` bereitgestellt werden, zum Beispiel ```sshflags=`-i <keyfile>` ```.

    In einer All-to-All-Topologie (die Standardkonfiguration) verbinden sich alle Worker über einfache TCP-Sockets miteinander. Die Sicherheitsrichtlinie auf den Clusterknoten muss daher eine freie Konnektivität zwischen den Workern für den Bereich der ephemeral Ports (variiert je nach Betriebssystem) gewährleisten.

    Die Sicherung und Verschlüsselung aller Mitarbeiter-Mitarbeiter-Verbindungen (über SSH) oder die Verschlüsselung einzelner Nachrichten kann über einen benutzerdefinierten `ClusterManager` erfolgen.
  * Wenn Sie `multiplex=true` als Option zu [`addprocs`](@ref) angeben, wird SSH-Multiplexing verwendet, um einen Tunnel zwischen dem Master und den Arbeitern zu erstellen. Wenn Sie SSH-Multiplexing selbst konfiguriert haben und die Verbindung bereits hergestellt wurde, wird SSH-Multiplexing unabhängig von der `multiplex`-Option verwendet. Wenn Multiplexing aktiviert ist, wird das Forwarding durch die Verwendung der bestehenden Verbindung (`-O forward`-Option in ssh) festgelegt. Dies ist vorteilhaft, wenn Ihre Server eine Passwortauthentifizierung erfordern; Sie können die Authentifizierung in Julia vermeiden, indem Sie sich vor `4d61726b646f776e2e436f64652822222c202261646470726f63732229_40726566` auf dem Server anmelden. Der Steuerungssocket befindet sich während der Sitzung unter `~/.ssh/julia-%r@%h:%p`, es sei denn, die bestehende Multiplexing-Verbindung wird verwendet. Beachten Sie, dass die Bandbreite begrenzt sein kann, wenn Sie mehrere Prozesse auf einem Knoten erstellen und Multiplexing aktivieren, da in diesem Fall die Prozesse eine einzige Multiplexing-TCP-Verbindung teilen.

### [Cluster Cookie](@id man-cluster-cookie)

Alle Prozesse in einem Cluster teilen sich dasselbe Cookie, das standardmäßig ein zufällig generierter String im Masterprozess ist:

  * [`cluster_cookie()`](@ref) gibt das Cookie zurück, während `cluster_cookie(cookie)()` es setzt und das neue Cookie zurückgibt.
  * Alle Verbindungen sind auf beiden Seiten authentifiziert, um sicherzustellen, dass nur von dem Master gestartete Worker miteinander verbunden werden dürfen.
  * Das Cookie kann beim Start an die Worker über das Argument `--worker=<cookie>` übergeben werden. Wenn das Argument `--worker` ohne das Cookie angegeben wird, versucht der Worker, das Cookie von seinem Standard-Eingang ([`stdin`](@ref)) zu lesen. Der `stdin` wird sofort geschlossen, nachdem das Cookie abgerufen wurde.
  * `ClusterManager`s können das Cookie auf dem Master abrufen, indem sie [`cluster_cookie()`](@ref) aufrufen. Cluster-Manager, die den Standard-TCP/IP-Transport nicht verwenden (und daher `--worker` nicht angeben), müssen `init_worker(cookie, manager)` mit demselben Cookie wie auf dem Master aufrufen.

Beachten Sie, dass Umgebungen, die höhere Sicherheitsstufen erfordern, dies über einen benutzerdefinierten `ClusterManager` implementieren können. Zum Beispiel können Cookies vorab geteilt werden und müssen daher nicht als Startargument angegeben werden.

## Specifying Network Topology (Experimental)

Das Schlüsselwortargument `topology`, das an [`addprocs`](@ref) übergeben wird, wird verwendet, um anzugeben, wie die Arbeiter miteinander verbunden sein müssen:

  * `:all_to_all`, der Standard: Alle Arbeiter sind miteinander verbunden.
  * `:master_worker`: Nur der Treiberprozess, d.h. `pid` 1, hat Verbindungen zu den Arbeitern.
  * `:custom`: Die `launch`-Methode des Cluster-Managers gibt die Verbindungs-Topologie über die Felder `ident` und `connect_idents` in `WorkerConfig` an. Ein Worker mit einer vom Cluster-Manager bereitgestellten Identität `ident` wird sich mit allen in `connect_idents` angegebenen Workern verbinden.

Das Schlüsselwort-Argument `lazy=true|false` betrifft nur die `topology`-Option `:all_to_all`. Wenn `true`, startet der Cluster mit dem Master, der mit allen Arbeitern verbunden ist. Spezifische Verbindungen zwischen Arbeitern werden bei der ersten Remote-Aufruf zwischen zwei Arbeitern hergestellt. Dies hilft, die anfänglichen Ressourcen, die für die Kommunikation innerhalb des Clusters zugewiesen werden, zu reduzieren. Verbindungen werden je nach den Laufzeitanforderungen eines parallelen Programms eingerichtet. Der Standardwert für `lazy` ist `true`.

Derzeit führt das Senden einer Nachricht zwischen nicht verbundenen Arbeitern zu einem Fehler. Dieses Verhalten, ebenso wie die Funktionalität und die Schnittstelle, sollte als experimentell betrachtet werden und kann sich in zukünftigen Versionen ändern.

## Noteworthy external packages

Außer der Parallelität von Julia gibt es viele externe Pakete, die erwähnt werden sollten. Zum Beispiel ist [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) ein Julia-Wrapper für das `MPI`-Protokoll, [`Dagger.jl`](https://github.com/JuliaParallel/Dagger.jl) bietet Funktionalitäten ähnlich wie Pythons [Dask](https://dask.org/), und [`DistributedArrays.jl`](https://github.com/JuliaParallel/Distributedarrays.jl) bietet Array-Operationen, die über Arbeiter verteilt sind, wie [outlined above](@ref man-shared-arrays).

Es muss auf Julias GPU-Programmier-Ökosystem hingewiesen werden, das Folgendes umfasst:

1. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) umschließt die verschiedenen CUDA-Bibliotheken und unterstützt das Kompilieren von Julia-Kernen für Nvidia-GPUs.
2. [oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl) umschließt das einheitliche Programmiermodell von oneAPI und unterstützt die Ausführung von Julia-Kernen auf unterstützten Beschleunigern. Derzeit wird nur Linux unterstützt.
3. [AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl) umschließt die AMD ROCm-Bibliotheken und unterstützt das Kompilieren von Julia-Kernels für AMD-GPUs. Derzeit wird nur Linux unterstützt.
4. Hochlevelige Bibliotheken wie [KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl), [Tullio.jl](https://github.com/mcabbott/Tullio.jl) und [ArrayFire.jl](https://github.com/JuliaComputing/ArrayFire.jl).

Im folgenden Beispiel werden wir sowohl `DistributedArrays.jl` als auch `CUDA.jl` verwenden, um ein Array über mehrere Prozesse zu verteilen, indem wir es zuerst durch `distribute()` und `CuArray()` umwandeln.

Erinnere dich daran, beim Importieren von `DistributedArrays.jl` es über alle Prozesse hinweg mit [`@everywhere`](@ref) zu importieren.

```julia-repl
$ ./julia -p 4

julia> addprocs()

julia> @everywhere using DistributedArrays

julia> using CUDA

julia> B = ones(10_000) ./ 2;

julia> A = ones(10_000) .* π;

julia> C = 2 .* A ./ B;

julia> all(C .≈ 4*π)
true

julia> typeof(C)
Array{Float64,1}

julia> dB = distribute(B);

julia> dA = distribute(A);

julia> dC = 2 .* dA ./ dB;

julia> all(dC .≈ 4*π)
true

julia> typeof(dC)
DistributedArrays.DArray{Float64,1,Array{Float64,1}}

julia> cuB = CuArray(B);

julia> cuA = CuArray(A);

julia> cuC = 2 .* cuA ./ cuB;

julia> all(cuC .≈ 4*π);
true

julia> typeof(cuC)
CuArray{Float64,1}
```

Im folgenden Beispiel werden wir sowohl `DistributedArrays.jl` als auch `CUDA.jl` verwenden, um ein Array über mehrere Prozesse zu verteilen und eine generische Funktion darauf aufzurufen.

```julia
function power_method(M, v)
    for i in 1:100
        v = M*v
        v /= norm(v)
    end

    return v, norm(M*v) / norm(v)  # or  (M*v) ./ v
end
```

`power_method` erstellt wiederholt einen neuen Vektor und normalisiert ihn. Wir haben keinen Typensignatur in der Funktionsdeklaration angegeben, lassen Sie uns sehen, ob es mit den oben genannten Datentypen funktioniert:

```julia-repl
julia> M = [2. 1; 1 1];

julia> v = rand(2)
2-element Array{Float64,1}:
0.40395
0.445877

julia> power_method(M,v)
([0.850651, 0.525731], 2.618033988749895)

julia> cuM = CuArray(M);

julia> cuv = CuArray(v);

julia> curesult = power_method(cuM, cuv);

julia> typeof(curesult)
CuArray{Float64,1}

julia> dM = distribute(M);

julia> dv = distribute(v);

julia> dC = power_method(dM, dv);

julia> typeof(dC)
Tuple{DistributedArrays.DArray{Float64,1,Array{Float64,1}},Float64}
```

Um diesen kurzen Einblick in externe Pakete zu beenden, können wir `MPI.jl` betrachten, einen Julia-Wrapper des MPI-Protokolls. Da es zu lange dauern würde, jede innere Funktion zu betrachten, wäre es besser, einfach den Ansatz zu schätzen, der zur Implementierung des Protokolls verwendet wurde.

Betrachten Sie dieses Spielzeug-Skript, das einfach jeden Unterprozess aufruft, seine Rangfolge instanziiert und wenn der Master-Prozess erreicht ist, die Summe der Ränge berechnet.

```julia
import MPI

MPI.Init()

comm = MPI.COMM_WORLD
MPI.Barrier(comm)

root = 0
r = MPI.Comm_rank(comm)

sr = MPI.Reduce(r, MPI.SUM, root, comm)

if(MPI.Comm_rank(comm) == root)
   @printf("sum of ranks: %s\n", sr)
end

MPI.Finalize()
```

```
mpirun -np 4 ./julia example.jl
```

[^1]: In this context, MPI refers to the MPI-1 standard. Beginning with MPI-2, the MPI standards committee introduced a new set of communication mechanisms, collectively referred to as Remote Memory Access (RMA). The motivation for adding rma to the MPI standard was to facilitate one-sided communication patterns. For additional information on the latest MPI standard, see [https://mpi-forum.org/docs](https://mpi-forum.org/docs).

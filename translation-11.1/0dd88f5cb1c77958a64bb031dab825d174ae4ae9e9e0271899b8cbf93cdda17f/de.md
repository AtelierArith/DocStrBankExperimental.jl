# Profiling

Das `Profile`-Modul bietet Werkzeuge, um Entwicklern zu helfen, die Leistung ihres Codes zu verbessern. Bei der Verwendung werden Messungen des laufenden Codes durchgeführt und Ausgaben erzeugt, die Ihnen helfen, zu verstehen, wie viel Zeit auf einzelnen Zeilen verbracht wird. Die häufigste Verwendung besteht darin, "Engpässe" als Ziele für die Optimierung zu identifizieren.

`Profil` implementiert das, was als "Sampling" bekannt ist, oder [statistical profiler](https://en.wikipedia.org/wiki/Profiling_(computer_programming)). Es funktioniert, indem es regelmäßig einen Backtrace während der Ausführung einer beliebigen Aufgabe aufnimmt. Jeder Backtrace erfasst die aktuell laufende Funktion und die Zeilennummer sowie die vollständige Kette von Funktionsaufrufen, die zu dieser Zeile geführt haben, und ist somit ein "Schnappschuss" des aktuellen Ausführungszustands.

Wenn ein großer Teil Ihrer Laufzeit mit der Ausführung einer bestimmten Codezeile verbracht wird, wird diese Zeile häufig in der Menge aller Rückverfolgungen angezeigt. Mit anderen Worten, die "Kosten" einer bestimmten Zeile – oder besser gesagt, die Kosten der Abfolge von Funktionsaufrufen bis zu und einschließlich dieser Zeile – sind proportional dazu, wie oft sie in der Menge aller Rückverfolgungen erscheint.

Ein Sampling-Profiling-Tool bietet keine vollständige Zeilen-für-Zeilen-Abdeckung, da die Backtraces in Intervallen erfolgen (standardmäßig 1 ms auf Unix-Systemen und 10 ms auf Windows, obwohl die tatsächliche Planung von der Last des Betriebssystems abhängt). Darüber hinaus, wie weiter unten erörtert, sind die Daten, die von einem Sampling-Profiling-Tool gesammelt werden, aufgrund der Tatsache, dass Proben an einer spärlichen Teilmenge aller Ausführungspunkte gesammelt werden, statistischem Rauschen unterworfen.

Trotz dieser Einschränkungen haben Sampling-Profiler erhebliche Stärken:

  * Sie müssen keine Änderungen an Ihrem Code vornehmen, um Zeitmessungen durchzuführen.
  * Es kann in Julias Kerncode und sogar (optional) in C- und Fortran-Bibliotheken profilieren.
  * Durch das Ausführen von "selten" gibt es sehr wenig Leistungsüberhead; während des Profilings kann Ihr Code nahezu mit nativer Geschwindigkeit ausgeführt werden.

Aus diesen Gründen wird empfohlen, dass Sie den integrierten Sampling-Profilierer ausprobieren, bevor Sie alternative Optionen in Betracht ziehen.

## Basic usage

Lass uns mit einem einfachen Testfall arbeiten:

```julia-repl
julia> function myfunc()
           A = rand(200, 200, 400)
           maximum(A)
       end
```

Es ist eine gute Idee, den Code, den Sie profilieren möchten, zunächst mindestens einmal auszuführen (es sei denn, Sie möchten Julias JIT-Compiler profilieren):

```julia-repl
julia> myfunc() # run once to force compilation
```

Jetzt sind wir bereit, diese Funktion zu profilieren:

```julia-repl
julia> using Profile

julia> @profile myfunc()
```

Um die Profilierungsergebnisse zu sehen, gibt es mehrere grafische Browser. Eine "Familie" von Visualisierern basiert auf [FlameGraphs.jl](https://github.com/timholy/FlameGraphs.jl), wobei jedes Familienmitglied eine andere Benutzeroberfläche bietet:

  * [VS Code](https://www.julia-vscode.org/) ist eine vollständige IDE mit integrierter Unterstützung für die Profildarstellung.
  * [ProfileView.jl](https://github.com/timholy/ProfileView.jl) ist ein eigenständiger Visualisierer, der auf GTK basiert.
  * [ProfileVega.jl](https://github.com/davidanthoff/ProfileVega.jl) verwendet VegaLight und integriert sich gut mit Jupyter-Notebooks.
  * [StatProfilerHTML.jl](https://github.com/tkluck/StatProfilerHTML.jl) erzeugt HTML und präsentiert einige zusätzliche Zusammenfassungen und integriert sich auch gut mit Jupyter-Notebooks.
  * [ProfileSVG.jl](https://github.com/timholy/ProfileSVG.jl) rendert SVG
  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl) dient als lokale Website zur Inspektion von Grafiken, Flamegraphs und mehr.
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) ist eine auf HTML-Canvas basierende Profilansicht-Benutzeroberfläche, die von [Julia VS Code extension](https://www.julia-vscode.org/) verwendet wird, aber auch interaktive HTML-Dateien generieren kann.

Ein völlig unabhängiger Ansatz zur Profildarstellung ist [PProf.jl](https://github.com/vchuravy/PProf.jl), der das externe Tool `pprof` verwendet.

Hier verwenden wir jedoch die textbasierte Anzeige, die mit der Standardbibliothek geliefert wird:

```julia-repl
julia> Profile.print()
80 ./event.jl:73; (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
 80 ./REPL.jl:97; macro expansion
  80 ./REPL.jl:66; eval_user_input(::Any, ::Base.REPL.REPLBackend)
   80 ./boot.jl:235; eval(::Module, ::Any)
    80 ./<missing>:?; anonymous
     80 ./profile.jl:23; macro expansion
      52 ./REPL[1]:2; myfunc()
       38 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type{B...
        38 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr{F...
       14 ./random.jl:278; rand
        14 ./random.jl:277; rand
         14 ./random.jl:366; rand
          14 ./random.jl:369; rand
      28 ./REPL[1]:3; myfunc()
       28 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinear,...
        3  ./reduce.jl:426; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
        25 ./reduce.jl:428; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
```

Jede Zeile dieser Anzeige repräsentiert einen bestimmten Punkt (Zeilennummer) im Code. Einrückungen werden verwendet, um die geschachtelte Reihenfolge der Funktionsaufrufe anzuzeigen, wobei stärker eingerückte Zeilen tiefer in der Reihenfolge der Aufrufe liegen. In jeder Zeile ist das erste "Feld" die Anzahl der Backtraces (Proben), die *an dieser Zeile oder in beliebigen Funktionen, die von dieser Zeile ausgeführt werden, genommen wurden*. Das zweite Feld ist der Dateiname und die Zeilennummer und das dritte Feld ist der Funktionsname. Beachten Sie, dass sich die spezifischen Zeilennummern ändern können, wenn sich Julias Code ändert; wenn Sie folgen möchten, ist es am besten, dieses Beispiel selbst auszuführen.

In diesem Beispiel können wir sehen, dass die oberste Funktion, die aufgerufen wird, sich in der Datei `event.jl` befindet. Dies ist die Funktion, die die REPL ausführt, wenn Sie Julia starten. Wenn Sie Zeile 97 von `REPL.jl` untersuchen, werden Sie sehen, dass hier die Funktion `eval_user_input()` aufgerufen wird. Dies ist die Funktion, die das, was Sie in der REPL eingeben, auswertet, und da wir interaktiv arbeiten, wurden diese Funktionen aufgerufen, als wir `@profile myfunc()` eingegeben haben. Die nächste Zeile spiegelt Aktionen wider, die im [`@profile`](@ref) Makro durchgeführt wurden.

Die erste Zeile zeigt, dass 80 Backtraces in Zeile 73 von `event.jl` aufgenommen wurden, aber es ist nicht so, dass diese Zeile für sich genommen "teuer" war: Die dritte Zeile zeigt, dass alle 80 dieser Backtraces tatsächlich innerhalb des Aufrufs von `eval_user_input` ausgelöst wurden, und so weiter. Um herauszufinden, welche Operationen tatsächlich Zeit in Anspruch nehmen, müssen wir tiefer in die Aufrufkette schauen.

Die erste "wichtige" Zeile in diesem Output ist diese:

```
52 ./REPL[1]:2; myfunc()
```

`REPL` bezieht sich darauf, dass wir `myfunc` im REPL definiert haben, anstatt es in eine Datei zu schreiben; wenn wir eine Datei verwendet hätten, würde dies den Dateinamen anzeigen. Die `[1]` zeigt an, dass die Funktion `myfunc` der erste Ausdruck war, der in dieser REPL-Sitzung ausgewertet wurde. Zeile 2 von `myfunc()` enthält den Aufruf von `rand`, und es gab 52 (von 80) Rückverfolgungen, die an dieser Stelle auftraten. Darunter sehen Sie einen Aufruf von `dsfmt_fill_array_close_open!` innerhalb von `dSFMT.jl`.

Ein wenig weiter unten siehst du:

```
28 ./REPL[1]:3; myfunc()
```

Zeile 3 von `myfunc` enthält den Aufruf von `maximum`, und es wurden hier 28 (von 80) Rückverfolgungen gemacht. Darunter sehen Sie die spezifischen Stellen in `base/reduce.jl`, die die zeitaufwändigen Operationen in der `maximum`-Funktion für diesen Datentyp durchführen.

Insgesamt können wir vorläufig schlussfolgern, dass das Generieren der Zufallszahlen ungefähr doppelt so teuer ist wie das Finden des maximalen Elements. Wir könnten unser Vertrauen in dieses Ergebnis erhöhen, indem wir mehr Proben sammeln:

```julia-repl
julia> @profile (for i = 1:100; myfunc(); end)

julia> Profile.print()
[....]
 3821 ./REPL[1]:2; myfunc()
  3511 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type...
   3511 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr...
  310  ./random.jl:278; rand
   [....]
 2893 ./REPL[1]:3; myfunc()
  2893 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinea...
   [....]
```

Im Allgemeinen, wenn Sie `N` Proben an einer Linie gesammelt haben, können Sie eine Unsicherheit in der Größenordnung von `sqrt(N)` erwarten (abgesehen von anderen Geräuschquellen, wie z.B. wie beschäftigt der Computer mit anderen Aufgaben ist). Die Hauptausnahme von dieser Regel ist die Speicherbereinigung, die selten läuft, aber tendenziell ziemlich teuer ist. (Da Julias Garbage Collector in C geschrieben ist, können solche Ereignisse mit dem `C=true` Ausgabemodus, der unten beschrieben ist, oder durch die Verwendung von [ProfileView.jl](https://github.com/timholy/ProfileView.jl) erkannt werden.)

Dies veranschaulicht den standardmäßigen "Baum"-Dump; eine Alternative ist der "flache" Dump, der Zählungen unabhängig von ihrer Verschachtelung akkumuliert:

```julia-repl
julia> Profile.print(format=:flat)
 Count File          Line Function
  6714 ./<missing>     -1 anonymous
  6714 ./REPL.jl       66 eval_user_input(::Any, ::Base.REPL.REPLBackend)
  6714 ./REPL.jl       97 macro expansion
  3821 ./REPL[1]        2 myfunc()
  2893 ./REPL[1]        3 myfunc()
  6714 ./REPL[7]        1 macro expansion
  6714 ./boot.jl      235 eval(::Module, ::Any)
  3511 ./dSFMT.jl      84 dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_s...
  6714 ./event.jl      73 (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
  6714 ./profile.jl    23 macro expansion
  3511 ./random.jl    431 rand!(::MersenneTwister, ::Array{Float64,3}, ::In...
   310 ./random.jl    277 rand
   310 ./random.jl    278 rand
   310 ./random.jl    366 rand
   310 ./random.jl    369 rand
  2893 ./reduce.jl    270 _mapreduce(::Base.#identity, ::Base.#scalarmax, :...
     5 ./reduce.jl    420 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
   253 ./reduce.jl    426 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
  2592 ./reduce.jl    428 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
    43 ./reduce.jl    429 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
```

Wenn Ihr Code Rekursion enthält, kann ein potenziell verwirrender Punkt sein, dass eine Zeile in einer "Kind"-Funktion mehr Zählungen ansammeln kann, als es insgesamt Rückverfolgungen gibt. Betrachten Sie die folgenden Funktionsdefinitionen:

```julia
dumbsum(n::Integer) = n == 1 ? 1 : 1 + dumbsum(n-1)
dumbsum3() = dumbsum(3)
```

Wenn Sie `dumbsum3` profilieren würden und ein Backtrace erstellt wurde, während es `dumbsum(1)` ausführte, würde der Backtrace folgendermaßen aussehen:

```julia
dumbsum3
    dumbsum(3)
        dumbsum(2)
            dumbsum(1)
```

Folglich erhält diese Kindfunktion 3 Zählungen, obwohl der Elternteil nur eine erhält. Die "Baum"-Darstellung macht dies viel klarer, und aus diesem Grund (unter anderem) ist sie wahrscheinlich die nützlichste Art, die Ergebnisse zu betrachten.

## Accumulation and clearing

Die Ergebnisse von [`@profile`](@ref) sammeln sich in einem Puffer; wenn Sie mehrere Codeabschnitte unter `4d61726b646f776e2e436f64652822222c20224070726f66696c652229_40726566` ausführen, dann wird [`Profile.print()`](@ref) Ihnen die kombinierten Ergebnisse anzeigen. Dies kann sehr nützlich sein, aber manchmal möchten Sie von vorne beginnen; das können Sie mit [`Profile.clear()`](@ref) tun.

## Options for controlling the display of profile results

[`Profile.print`](@ref) hat mehr Optionen als wir bisher beschrieben haben. Lassen Sie uns die vollständige Deklaration ansehen:

```julia
function print(io::IO = stdout, data = fetch(); kwargs...)
```

Lass uns zuerst die beiden Positionsargumente und später die Schlüsselwortargumente besprechen:

  * `io` – Ermöglicht es Ihnen, die Ergebnisse in einem Puffer zu speichern, z. B. in einer Datei, aber standardmäßig wird in `stdout` (der Konsole) ausgegeben.
  * `data` – Enthält die Daten, die Sie analysieren möchten; standardmäßig wird dies von [`Profile.fetch()`](@ref) abgerufen, das die Rückverfolgungen aus einem vorab zugewiesenen Puffer extrahiert. Wenn Sie beispielsweise den Profiler profilieren möchten, könnten Sie sagen:

    ```julia
    data = copy(Profile.fetch())
    Profile.clear()
    @profile Profile.print(stdout, data) # Prints the previous results
    Profile.print()                      # Prints results from Profile.print()
    ```

Die Schlüsselwortargumente können jede Kombination aus Folgendem sein:

  * `format` – Wie oben eingeführt, bestimmt, ob Backtraces mit (Standard, `:tree`) oder ohne (`:flat`) Einrückung, die die Baumstruktur anzeigt, gedruckt werden.
  * `C` – Wenn `true`, werden Rückverfolgungen aus C- und Fortran-Code angezeigt (normalerweise sind sie ausgeschlossen). Versuchen Sie, das einführende Beispiel mit `Profile.print(C = true)` auszuführen. Dies kann äußerst hilfreich sein, um zu entscheiden, ob es Julia-Code oder C-Code ist, der einen Engpass verursacht; das Setzen von `C = true` verbessert auch die Interpretierbarkeit der Verschachtelung, auf Kosten längerer Profil-Dumps.
  * `combine` – Einige Codezeilen enthalten mehrere Operationen; zum Beispiel enthält `s += A[i]` sowohl einen Arrayverweis (`A[i]`) als auch eine Summenoperation. Diese entsprechen verschiedenen Zeilen im generierten Maschinencode, und daher können während der Rückverfolgung auf dieser Zeile zwei oder mehr verschiedene Adressen erfasst werden. `combine = true` fasst sie zusammen und ist wahrscheinlich das, was Sie typischerweise möchten, aber Sie können eine Ausgabe separat für jeden eindeutigen Instruktionszeiger mit `combine = false` generieren.
  * `maxdepth` – Begrenzung von Frames auf eine Tiefe, die höher ist als `maxdepth` im `:tree`-Format.
  * `sortedby` – Steuert die Reihenfolge im `:flat`-Format. `:filefuncline` (Standard) sortiert nach der Quellzeile, während `:count` in der Reihenfolge der Anzahl gesammelter Proben sortiert.
  * `noisefloor` – Begrenzungen von Frames, die unter dem heuristischen Rauschboden der Probe liegen (gilt nur für das Format `:tree`). Ein empfohlener Wert, den Sie ausprobieren können, ist 2.0 (der Standardwert ist 0). Dieses Parameter verbirgt Proben, für die `n <= noisefloor * √N`, wobei `n` die Anzahl der Proben in dieser Zeile und `N` die Anzahl der Proben für den Aufrufer ist.
  * `mincount` – Begrenzt Frames mit weniger als `mincount` Vorkommen.

Datei/Funktionsnamen werden manchmal abgeschnitten (mit `...`), und die Einrückung wird mit einem `+n` am Anfang abgekürzt, wobei `n` die Anzahl der zusätzlichen Leerzeichen ist, die eingefügt worden wären, wenn Platz gewesen wäre. Wenn Sie ein vollständiges Profil von tief verschachteltem Code möchten, ist es oft eine gute Idee, in eine Datei zu speichern, indem Sie eine breite `displaysize` in einem [`IOContext`](@ref) verwenden:

```julia
open("/tmp/prof.txt", "w") do s
    Profile.print(IOContext(s, :displaysize => (24, 500)))
end
```

## Configuration

[`@profile`](@ref) sammelt nur Backtraces, und die Analyse erfolgt, wenn Sie [`Profile.print()`](@ref) aufrufen. Bei einer lang laufenden Berechnung ist es durchaus möglich, dass der vorab zugewiesene Puffer zum Speichern von Backtraces gefüllt wird. Wenn das passiert, stoppen die Backtraces, aber Ihre Berechnung läuft weiter. Infolgedessen könnten Sie einige wichtige Profildaten verpassen (Sie erhalten eine Warnung, wenn das passiert).

Sie können die relevanten Parameter auf diese Weise abrufen und konfigurieren:

```julia
Profile.init() # returns the current settings
Profile.init(n = 10^7, delay = 0.01)
```

`n` ist die Gesamtzahl der Instruktionszeiger, die Sie speichern können, mit einem Standardwert von `10^6`. Wenn Ihr typischer Backtrace 20 Instruktionszeiger umfasst, können Sie 50000 Backtraces sammeln, was eine statistische Unsicherheit von weniger als 1% nahelegt. Dies könnte für die meisten Anwendungen ausreichend sein.

Folglich müssen Sie wahrscheinlich `delay` anpassen, das in Sekunden angegeben wird und die Zeit festlegt, die Julia zwischen den Snapshots hat, um die angeforderten Berechnungen durchzuführen. Ein sehr lang laufender Job benötigt möglicherweise keine häufigen Backtraces. Die Standardeinstellung ist `delay = 0.001`. Natürlich können Sie die Verzögerung sowohl verringern als auch erhöhen; jedoch wächst der Overhead des Profilings, sobald die Verzögerung ähnlich der Zeit wird, die benötigt wird, um einen Backtrace zu erstellen (~30 Mikrosekunden auf dem Laptop des Autors).

## Memory allocation analysis

Eine der häufigsten Techniken zur Verbesserung der Leistung besteht darin, die Speicherzuweisung zu reduzieren. Julia bietet mehrere Werkzeuge, um dies zu messen:

### `@time`

Der gesamte Betrag der Zuweisung kann mit [`@time`](@ref), [`@allocated`](@ref) und [`@allocations`](@ref) gemessen werden, und spezifische Zeilen, die die Zuweisung auslösen, können oft aus dem Profiling abgeleitet werden, basierend auf den Kosten der Müllsammlung, die diese Zeilen verursachen. Manchmal ist es jedoch effizienter, die Menge des von jeder Codezeile zugewiesenen Speichers direkt zu messen.

### GC Logging

Während [`@time`](@ref) hochrangige Statistiken über die Speichernutzung und die Garbage Collection im Verlauf der Auswertung eines Ausdrucks protokolliert, kann es nützlich sein, jedes Ereignis der Garbage Collection zu protokollieren, um ein intuitives Gefühl dafür zu bekommen, wie oft der Garbage Collector läuft, wie lange er jedes Mal läuft und wie viel Müll er jedes Mal sammelt. Dies kann mit [`GC.enable_logging(true)`](@ref) aktiviert werden, was dazu führt, dass Julia jedes Mal, wenn eine Garbage Collection stattfindet, in stderr protokolliert.

### [Allocation Profiler](@id allocation-profiler)

!!! compat "Julia 1.8"
    Diese Funktionalität erfordert mindestens Julia 1.8.


Der Allocationsprofiler zeichnet den Stack-Trace, den Typ und die Größe jeder Zuweisung auf, während er läuft. Er kann mit [`Profile.Allocs.@profile`](@ref) aufgerufen werden.

Diese Informationen über die Zuweisungen werden als ein Array von `Alloc`-Objekten zurückgegeben, das in einem `AllocResults`-Objekt eingewickelt ist. Der beste Weg, diese zu visualisieren, ist derzeit mit den [PProf.jl](https://github.com/JuliaPerf/PProf.jl) und [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) Paketen, die die Aufrufstapel visualisieren können, die die meisten Zuweisungen vornehmen.

Der Allocationsprofiler hat erhebliche Overhead, daher kann ein `sample_rate`-Argument übergeben werden, um ihn zu beschleunigen, indem einige Zuweisungen übersprungen werden. Das Übergeben von `sample_rate=1.0` wird alles aufzeichnen (was langsam ist); `sample_rate=0.1` wird nur 10% der Zuweisungen aufzeichnen (schneller) usw.

!!! compat "Julia 1.11"
    Ältere Versionen von Julia konnten in allen Fällen keine Typen erfassen. In älteren Versionen von Julia, wenn Sie eine Zuweisung des Typs `Profile.Allocs.UnknownType` sehen, bedeutet dies, dass der Profiler nicht weiß, welcher Typ von Objekt zugewiesen wurde. Dies geschah hauptsächlich, wenn die Zuweisung aus generiertem Code stammte, der vom Compiler erzeugt wurde. Siehe [issue #43688](https://github.com/JuliaLang/julia/issues/43688) für weitere Informationen.

    Seit Julia 1.11 sollte jede Zuweisung einen Typ gemeldet haben.


Für weitere Informationen zur Verwendung dieses Tools siehe den folgenden Vortrag von JuliaCon 2022: https://www.youtube.com/watch?v=BFvpwC8hEWQ

##### Allocation Profiler Example

In diesem einfachen Beispiel verwenden wir PProf, um das Alloc-Profil zu visualisieren. Sie könnten stattdessen ein anderes Visualisierungstool verwenden. Wir sammeln das Profil (unter Angabe einer Stichprobenrate) und visualisieren es dann.

```julia
using Profile, PProf
Profile.Allocs.clear()
Profile.Allocs.@profile sample_rate=0.0001 my_function()
PProf.Allocs.pprof()
```

Hier ist ein detaillierteres Beispiel, das zeigt, wie wir die Abtastrate anpassen können. Eine gute Anzahl von Proben, die man anstreben sollte, liegt bei etwa 1 - 10 Tausend. Zu viele, und der Profilvisualisierer kann überfordert werden, und das Profiling wird langsam. Zu wenige, und man hat keine repräsentative Probe.

```julia-repl
julia> import Profile

julia> @time my_function()  # Estimate allocations from a (second-run) of the function
  0.110018 seconds (1.50 M allocations: 58.725 MiB, 17.17% gc time)
500000

julia> Profile.Allocs.clear()

julia> Profile.Allocs.@profile sample_rate=0.001 begin   # 1.5 M * 0.001 = ~1.5K allocs.
           my_function()
       end
500000

julia> prof = Profile.Allocs.fetch();  # If you want, you can also manually inspect the results.

julia> length(prof.allocs)  # Confirm we have expected number of allocations.
1515

julia> using PProf  # Now, visualize with an external tool, like PProf or ProfileCanvas.

julia> PProf.Allocs.pprof(prof; from_c=false)  # You can optionally pass in a previously fetched profile result.
Analyzing 1515 allocation samples... 100%|████████████████████████████████| Time: 0:00:00
Main binary filename not available.
Serving web UI on http://localhost:62261
"alloc-profile.pb.gz"
```

Dann können Sie das Profil aufrufen, indem Sie zu http://localhost:62261 navigieren, und das Profil wird auf der Festplatte gespeichert. Siehe PProf-Paket für weitere Optionen.

##### Allocation Profiling Tips

Wie oben angegeben, streben Sie etwa 1-10 Tausend Proben in Ihrem Profil an.

Beachten Sie, dass wir gleichmäßig im Raum *aller Zuweisungen* sampeln und unsere Proben nicht nach der Größe der Zuweisung gewichten. Daher kann ein bestimmtes Zuweisungsprofil kein repräsentatives Profil dafür liefern, wo die meisten Bytes in Ihrem Programm zugewiesen werden, es sei denn, Sie haben `sample_rate=1` eingestellt.

Allokationen können direkt von Benutzern stammen, die Objekte konstruieren, können aber auch aus der Laufzeit kommen oder in kompilierten Code eingefügt werden, um Typinstabilität zu behandeln. Die Ansicht des "Quellcodes" kann hilfreich sein, um sie zu isolieren, und dann können andere externe Tools wie [`Cthulhu.jl`](https://github.com/JuliaDebug/Cthulhu.jl) nützlich sein, um die Ursache der Allokation zu identifizieren.

##### Allocation Profile Visualization Tools

Es gibt jetzt mehrere Profiling-Visualisierungstools, die alle Zuweisungsprofile anzeigen können. Hier ist eine kleine Liste einiger der wichtigsten, die wir kennen:

  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl)
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl)
  * VSCode's integrierter Profilvisualisierer (`@profview_allocs`) [Dokumentation erforderlich]
  * Die Ergebnisse direkt im REPL anzeigen

      * Sie können die Ergebnisse im REPL über [`Profile.Allocs.fetch()`](@ref) inspizieren, um den Stacktrace und den Typ jeder Zuweisung anzuzeigen.

#### Line-by-Line Allocation Tracking

Eine alternative Möglichkeit, Zuweisungen zu messen, besteht darin, Julia mit der Befehlszeilenoption `--track-allocation=<Einstellung>` zu starten, bei der Sie `none` (die Standardeinstellung, keine Zuweisungen messen), `user` (Speicherzuweisungen überall messen, außer im Kerncode von Julia) oder `all` (Speicherzuweisungen in jeder Zeile von Julia-Code messen) wählen können. Die Zuweisung wird für jede Zeile des kompilierten Codes gemessen. Wenn Sie Julia beenden, werden die kumulierten Ergebnisse in Textdateien mit der Endung `.mem`, die nach dem Dateinamen angehängt wird, im selben Verzeichnis wie die Quelldatei gespeichert. Jede Zeile listet die insgesamt zugewiesenen Bytes auf. Die [`Coverage` package](https://github.com/JuliaCI/Coverage.jl) enthält einige grundlegende Analysetools, zum Beispiel um die Zeilen nach der Anzahl der zugewiesenen Bytes zu sortieren.

Bei der Interpretation der Ergebnisse gibt es einige wichtige Details. Unter der `user`-Einstellung zeigt die erste Zeile jeder Funktion, die direkt aus der REPL aufgerufen wird, eine Zuweisung aufgrund von Ereignissen, die im REPL-Code selbst stattfinden. Bedeutender ist, dass die JIT-Kompilierung ebenfalls zu den Zuweisungszahlen beiträgt, da ein Großteil von Julias Compiler in Julia geschrieben ist (und die Kompilierung normalerweise Speicherzuweisungen erfordert). Das empfohlene Verfahren besteht darin, die Kompilierung zu erzwingen, indem Sie alle Befehle ausführen, die Sie analysieren möchten, und dann [`Profile.clear_malloc_data()`](@ref) aufrufen, um alle Zählungen der Zuweisungen zurückzusetzen. Schließlich führen Sie die gewünschten Befehle aus und beenden Julia, um die Erstellung der `.mem`-Dateien auszulösen.

!!! note
    `--track-allocation` ändert die Codegenerierung, um die Zuweisungen zu protokollieren, und daher können die Zuweisungen anders sein als ohne die Option. Wir empfehlen, stattdessen [allocation profiler](@ref allocation-profiler) zu verwenden.


## External Profiling

Derzeit unterstützt Julia `Intel VTune`, `OProfile` und `perf` als externe Profiling-Tools.

Je nach dem von Ihnen gewählten Tool, kompilieren Sie mit `USE_INTEL_JITEVENTS`, `USE_OPROFILE_JITEVENTS` und `USE_PERF_JITEVENTS`, die auf 1 in `Make.user` gesetzt sind. Mehrere Flags werden unterstützt.

Bevor Sie Julia ausführen, setzen Sie die Umgebungsvariable [`ENABLE_JITPROFILING`](@ref ENABLE_JITPROFILING) auf 1.

Jetzt haben Sie eine Vielzahl von Möglichkeiten, diese Werkzeuge einzusetzen! Zum Beispiel können Sie mit `OProfile` eine einfache Aufzeichnung versuchen:

```
>ENABLE_JITPROFILING=1 sudo operf -Vdebug ./julia test/fastmath.jl
>opreport -l `which ./julia`
```

Oder ähnlich mit `perf`:

```
$ ENABLE_JITPROFILING=1 perf record -o /tmp/perf.data --call-graph dwarf -k 1 ./julia /test/fastmath.jl
$ perf inject --jit --input /tmp/perf.data --output /tmp/perf-jit.data
$ perf report --call-graph -G -i /tmp/perf-jit.data
```

Es gibt viele weitere interessante Dinge, die Sie über Ihr Programm messen können. Um eine umfassende Liste zu erhalten, lesen Sie bitte die [Linux perf examples page](https://www.brendangregg.com/perf.html).

Denke daran, dass perf für jede Ausführung eine `perf.data`-Datei speichert, die selbst für kleine Programme ziemlich groß werden kann. Außerdem speichert das perf LLVM-Modul vorübergehend Debug-Objekte in `~/.debug/jit`, denke daran, diesen Ordner häufig zu bereinigen.

```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Logging/docs/src/index.md"
```

# [Logging](@id man-logging)

Das [`Logging`](@ref Logging.Logging)-Modul bietet eine Möglichkeit, die Historie und den Fortschritt einer Berechnung als Protokoll von Ereignissen aufzuzeichnen. Ereignisse werden erstellt, indem eine Protokollierungsanweisung in den Quellcode eingefügt wird, zum Beispiel:

```julia
@warn "Abandon printf debugging, all ye who enter here!"
┌ Warning: Abandon printf debugging, all ye who enter here!
└ @ Main REPL[1]:1
```

Das System bietet mehrere Vorteile gegenüber dem Verstreuen von `println()`-Aufrufen in Ihrem Quellcode. Erstens ermöglicht es Ihnen, die Sichtbarkeit und Präsentation von Nachrichten zu steuern, ohne den Quellcode bearbeiten zu müssen. Zum Beispiel im Gegensatz zu dem oben genannten `@warn`

```julia
@debug "The sum of some values $(sum(rand(100)))"
```

wird standardmäßig keine Ausgabe erzeugen. Darüber hinaus ist es sehr günstig, Debug-Anweisungen wie diese im Quellcode zu belassen, da das System die Auswertung der Nachricht vermeidet, wenn sie später ignoriert wird. In diesem Fall wird `sum(rand(100))` und die zugehörige String-Verarbeitung niemals ausgeführt, es sei denn, das Debug-Logging ist aktiviert.

Zweitens ermöglichen die Protokollierungswerkzeuge, beliebige Daten als eine Menge von Schlüssel-Wert-Paaren an jedes Ereignis anzuhängen. Dies ermöglicht es Ihnen, lokale Variablen und andere Programmzustände für eine spätere Analyse zu erfassen. Um beispielsweise die lokale Array-Variable `A` und die Summe eines Vektors `v` als den Schlüssel `s` anzuhängen, können Sie verwenden

```jldoctest
A = ones(Int, 4, 4)
v = ones(100)
@info "Some variables"  A  s=sum(v)

# output
┌ Info: Some variables
│   A =
│    4×4 Matrix{Int64}:
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
└   s = 100.0
```

Alle Protokollierungs-Makros `@debug`, `@info`, `@warn` und `@error` teilen gemeinsame Funktionen, die ausführlich in der Dokumentation für das allgemeinere Makro [`@logmsg`](@ref) beschrieben sind.

## Log event structure

Jedes Ereignis generiert mehrere Datenstücke, einige werden vom Benutzer bereitgestellt und einige automatisch extrahiert. Lassen Sie uns zunächst die benutzerdefinierten Daten untersuchen:

  * Das *Protokollniveau* ist eine breite Kategorie für die Nachricht, die für eine frühe Filterung verwendet wird. Es gibt mehrere Standardstufen des Typs [`LogLevel`](@ref); benutzerdefinierte Stufen sind ebenfalls möglich. Jede ist in ihrem Zweck unterschiedlich:

      * [`Logging.Debug`](@ref) (Protokollebene -1000) ist eine Information, die für den Entwickler des Programms bestimmt ist. Diese Ereignisse sind standardmäßig deaktiviert.
      * [`Logging.Info`](@ref) (Protokollstufe 0) dient allgemeinen Informationen für den Benutzer. Betrachten Sie es als eine Alternative zur direkten Verwendung von `println`.
      * [`Logging.Warn`](@ref) (Protokollstufe 1000) bedeutet, dass etwas nicht stimmt und wahrscheinlich Maßnahmen erforderlich sind, aber dass das Programm vorerst weiterhin funktioniert.
      * [`Logging.Error`](@ref) (Protokollebene 2000) bedeutet, dass etwas nicht stimmt und es unwahrscheinlich ist, dass es wiederhergestellt werden kann, zumindest nicht von diesem Teil des Codes. Oft ist dieses Protokollebene nicht erforderlich, da das Auslösen einer Ausnahme alle benötigten Informationen übermitteln kann.
  * Die *Nachricht* ist ein Objekt, das das Ereignis beschreibt. Nach Konvention werden `AbstractString`s, die als Nachrichten übergeben werden, als im Markdown-Format angenommen. Andere Typen werden mit `print(io, obj)` oder `string(obj)` für textbasierte Ausgaben und möglicherweise `show(io,mime,obj)` für andere Multimedia-Anzeigen, die im installierten Logger verwendet werden, angezeigt.
  * Optionale *Schlüssel-Wert-Paare* ermöglichen es, beliebige Daten an jedes Ereignis anzuhängen. Einige Schlüssel haben eine konventionelle Bedeutung, die die Art und Weise beeinflussen kann, wie ein Ereignis interpretiert wird (siehe [`@logmsg`](@ref)).

Das System generiert auch einige Standardinformationen für jedes Ereignis:

  * Das `Modul`, in dem das Logging-Makro erweitert wurde.
  * Die `Datei` und `Zeile`, in der das Logging-Makro im Quellcode auftritt.
  * Eine Nachricht `id`, die ein eindeutiger, fester Identifikator für die *Quellcode-Anweisung* ist, an der das Logging-Makro erscheint. Dieser Identifikator ist so konzipiert, dass er relativ stabil bleibt, selbst wenn sich der Quellcode der Datei ändert, solange die Logging-Anweisung selbst gleich bleibt.
  * Eine `Gruppe` für das Ereignis, die standardmäßig auf den Basisnamen der Datei ohne Erweiterung gesetzt ist. Dies kann verwendet werden, um Nachrichten feiner in Kategorien als das Protokollniveau zu gruppieren (zum Beispiel haben alle Abwertungswarnungen die Gruppe `:depwarn`), oder um logische Gruppierungen über oder innerhalb von Modulen zu erstellen.

Beachten Sie, dass einige nützliche Informationen wie die Veranstaltungszeit standardmäßig nicht enthalten sind. Dies liegt daran, dass solche Informationen teuer zu extrahieren sein können und auch *dynamisch* dem aktuellen Logger zur Verfügung stehen. Es ist einfach, eine [custom logger](@ref AbstractLogger-interface) zu definieren, um Ereignisdaten mit der Zeit, dem Backtrace, Werten globaler Variablen und anderen nützlichen Informationen nach Bedarf zu ergänzen.

## Processing log events

Wie Sie in den Beispielen sehen können, erwähnen die Protokollierungsanweisungen nicht, wohin Protokollereignisse gehen oder wie sie verarbeitet werden. Dies ist ein wichtiges Designelement, das das System zusammensetzbar und natürlich für die gleichzeitige Nutzung macht. Es erreicht dies, indem es zwei verschiedene Anliegen trennt:

  * *Das Erstellen* von Protokollereignissen liegt in der Verantwortung des Modulentwicklers, der entscheiden muss, wo Ereignisse ausgelöst werden und welche Informationen enthalten sein sollen.
  * *Verarbeitung* von Protokollereignissen — das heißt, Anzeige, Filterung, Aggregation und Aufzeichnung — ist das Anliegen des Anwendungsautors, der mehrere Module zu einer kooperierenden Anwendung zusammenbringen muss.

### Loggers

Die Verarbeitung von Ereignissen erfolgt durch einen *Logger*, der das erste Stück benutzerkonfigurierbaren Codes ist, das das Ereignis sieht. Alle Logger müssen Untertypen von [`AbstractLogger`](@ref) sein.

Wenn ein Ereignis ausgelöst wird, wird der entsprechende Logger gefunden, indem nach einem aufgabenlokalen Logger mit dem globalen Logger als Fallback gesucht wird. Die Idee dabei ist, dass der Anwendungscode weiß, wie Protokollereignisse verarbeitet werden sollten und irgendwo ganz oben im Aufrufstapel existiert. Daher sollten wir durch den Aufrufstapel nach oben schauen, um den Logger zu entdecken – das heißt, der Logger sollte *dynamisch scoping* sein. (Dies ist ein Gegensatz zu Protokollierungsframeworks, bei denen der Logger *lexikalisch scoping* ist; explizit vom Modulautor bereitgestellt oder als einfache globale Variable. In einem solchen System ist es umständlich, das Protokollieren zu steuern, während man Funktionalität aus mehreren Modulen zusammensetzt.)

Der globale Logger kann mit [`global_logger`](@ref) gesetzt werden, und task-lokale Logger werden mit [`with_logger`](@ref) gesteuert. Neu gestartete Aufgaben erben den Logger der übergeordneten Aufgabe.

Es gibt drei Logger-Typen, die von der Bibliothek bereitgestellt werden.  [`ConsoleLogger`](@ref) ist der Standard-Logger, den Sie beim Starten des REPL sehen. Er zeigt Ereignisse in einem lesbaren Textformat an und versucht, einfache, aber benutzerfreundliche Steuerung über Formatierung und Filterung zu bieten. [`NullLogger`](@ref) ist eine praktische Möglichkeit, alle Nachrichten nach Bedarf zu verwerfen; es ist das Logging-Äquivalent des [`devnull`](@ref) Streams. [`SimpleLogger`](@ref) ist ein sehr einfacher Textformatierungs-Logger, der hauptsächlich nützlich ist, um das Logging-System selbst zu debuggen.

Benutzerdefinierte Protokollierer sollten Überladungen für die Funktionen bereitstellen, die in der [reference section](@ref AbstractLogger-interface) beschrieben sind.

### Early filtering and message handling

Wenn ein Ereignis eintritt, erfolgen einige Schritte der frühen Filterung, um zu vermeiden, dass Nachrichten generiert werden, die verworfen werden.

1. Das Nachrichtenprotokollniveau wird mit einem globalen Mindestniveau (festgelegt über [`disable_logging`](@ref)) überprüft. Dies ist eine grobe, aber äußerst kostengünstige globale Einstellung.
2. Der aktuelle Logger-Zustand wird überprüft und das Nachrichtenlevel wird mit dem minimalen Level des Loggers verglichen, das durch den Aufruf von [`Logging.min_enabled_level`](@ref) gefunden wurde. Dieses Verhalten kann über Umgebungsvariablen überschrieben werden (mehr dazu später).
3. Die [`Logging.shouldlog`](@ref)-Funktion wird mit dem aktuellen Logger aufgerufen und nimmt einige minimale Informationen (Level, Modul, Gruppe, ID) entgegen, die statisch berechnet werden können. Am nützlichsten ist, dass `shouldlog` eine Ereignis-ID übergeben wird, die verwendet werden kann, um Ereignisse frühzeitig basierend auf einem zwischengespeicherten Prädikat abzulehnen.

Wenn all diese Überprüfungen bestanden sind, werden die Nachricht und die Schlüssel-Wert-Paare vollständig ausgewertet und über die [`Logging.handle_message`](@ref)-Funktion an den aktuellen Logger übergeben. `handle_message()` kann zusätzliche Filterungen vornehmen, wie erforderlich, und das Ereignis auf dem Bildschirm anzeigen, in eine Datei speichern usw.

Ausnahmen, die beim Generieren des Protokollereignisses auftreten, werden standardmäßig erfasst und protokolliert. Dies verhindert, dass einzelne fehlerhafte Ereignisse die Anwendung zum Absturz bringen, was hilfreich ist, wenn selten verwendete Debug-Ereignisse in einem Produktionssystem aktiviert werden. Dieses Verhalten kann pro Logger-Typ angepasst werden, indem [`Logging.catch_exceptions`](@ref) erweitert wird.

## Testing log events

Log events are a side effect of running normal code, but you might find yourself wanting to test particular informational messages and warnings. The `Test` module provides a [`@test_logs`](@ref) macro that can be used to pattern match against the log event stream.

## Environment variables

Die Nachrichtenfilterung kann durch die Umgebungsvariable [`JULIA_DEBUG`](@ref JULIA_DEBUG) beeinflusst werden und dient als einfache Möglichkeit, das Debug-Logging für eine Datei oder ein Modul zu aktivieren. Das Laden von Julia mit `JULIA_DEBUG=loading` aktiviert `@debug`-Protokollnachrichten in `loading.jl`. Zum Beispiel in Linux-Shells:

```
$ JULIA_DEBUG=loading julia -e 'using OhMyREPL'
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
[ Info: Recompiling stale cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji for module OhMyREPL
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/Tokenize.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
...
```

Unter Windows kann dasselbe im `CMD` erreicht werden, indem zuerst `set JULIA_DEBUG="loading"` ausgeführt wird, und in `Powershell` über `$env:JULIA_DEBUG="loading"`.

Ähnlich kann die Umgebungsvariable verwendet werden, um das Debug-Logging von Modulen, wie `Pkg`, oder Modulwurzeln zu aktivieren (siehe [`Base.moduleroot`](@ref)). Um alle Debug-Logs zu aktivieren, verwenden Sie den speziellen Wert `all`.

Um das Debug-Logging von der REPL aus zu aktivieren, setzen Sie `ENV["JULIA_DEBUG"]` auf den Namen des interessierenden Moduls. Funktionen, die in der REPL definiert sind, gehören zum Modul `Main`; das Logging für sie kann wie folgt aktiviert werden:

```julia-repl
julia> foo() = @debug "foo"
foo (generic function with 1 method)

julia> foo()

julia> ENV["JULIA_DEBUG"] = Main
Main

julia> foo()
┌ Debug: foo
└ @ Main REPL[1]:1

```

Verwenden Sie ein Komma als Trennzeichen, um das Debugging für mehrere Module zu aktivieren: `JULIA_DEBUG=loading,Main`.

## Examples

### Example: Writing log events to a file

Manchmal kann es nützlich sein, Protokollereignisse in eine Datei zu schreiben. Hier ist ein Beispiel, wie man einen aufgabenlokalen und globalen Logger verwendet, um Informationen in eine Textdatei zu schreiben:

```julia-repl
# Load the logging module
julia> using Logging

# Open a textfile for writing
julia> io = open("log.txt", "w+")
IOStream(<file log.txt>)

# Create a simple logger
julia> logger = SimpleLogger(io)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# Log a task-specific message
julia> with_logger(logger) do
           @info("a context specific log message")
       end

# Write all buffered messages to the file
julia> flush(io)

# Set the global logger to logger
julia> global_logger(logger)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# This message will now also be written to the file
julia> @info("a global log message")

# Close the file
julia> close(io)
```

### Example: Enable debug-level messages

Hier ist ein Beispiel für die Erstellung eines [`ConsoleLogger`](@ref), das alle Nachrichten mit einem Protokolllevel höher oder gleich [`Logging.Debug`](@ref) durchlässt.

```julia-repl
julia> using Logging

# Create a ConsoleLogger that prints any log messages with level >= Debug to stderr
julia> debuglogger = ConsoleLogger(stderr, Logging.Debug)

# Enable debuglogger for a task
julia> with_logger(debuglogger) do
           @debug "a context specific log message"
       end

# Set the global logger
julia> global_logger(debuglogger)
```

## Reference

### Logging module

```@docs
Logging.Logging
```

### Creating events

```@docs
Logging.@logmsg
Logging.LogLevel
Logging.Debug
Logging.Info
Logging.Warn
Logging.Error
Logging.BelowMinLevel
Logging.AboveMaxLevel
```

### [Processing events with AbstractLogger](@id AbstractLogger-interface)

Die Ereignisverarbeitung wird durch das Überschreiben von Funktionen gesteuert, die mit `AbstractLogger` verknüpft sind:

| Methods to implement                |                        | Brief description                            |
|:----------------------------------- |:---------------------- |:-------------------------------------------- |
| [`Logging.handle_message`](@ref)    |                        | Handle a log event                           |
| [`Logging.shouldlog`](@ref)         |                        | Early filtering of events                    |
| [`Logging.min_enabled_level`](@ref) |                        | Lower bound for log level of accepted events |
| **Optional methods**                | **Default definition** | **Brief description**                        |
| [`Logging.catch_exceptions`](@ref)  | `true`                 | Catch exceptions during event evaluation     |

```@docs
Logging.AbstractLogger
Logging.handle_message
Logging.shouldlog
Logging.min_enabled_level
Logging.catch_exceptions
Logging.disable_logging
```

### Using Loggers

Logger-Installation und -Inspektion:

```@docs
Logging.global_logger
Logging.with_logger
Logging.current_logger
```

Logger, die mit dem System geliefert werden:

```@docs
Logging.NullLogger
Logging.ConsoleLogger
Logging.SimpleLogger
```

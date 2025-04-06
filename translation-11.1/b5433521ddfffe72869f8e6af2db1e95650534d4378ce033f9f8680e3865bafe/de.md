```
@debug Nachricht  [key=value | value ...]
@info  Nachricht  [key=value | value ...]
@warn  Nachricht  [key=value | value ...]
@error Nachricht  [key=value | value ...]

@logmsg niveau nachricht [key=value | value ...]

Erstellen Sie einen Protokolleintrag mit einer informativen `Nachricht`.  Zur Vereinfachung sind vier Protokollierungs-Makros `@debug`, `@info`, `@warn` und `@error` definiert, die auf den standardmäßigen Schweregraden `Debug`, `Info`, `Warn` und `Error` protokollieren.  `@logmsg` ermöglicht es, `niveau` programmgesteuert auf jeden `LogLevel` oder benutzerdefinierte Protokollebene zu setzen.

`Nachricht` sollte ein Ausdruck sein, der zu einem String ausgewertet wird, der eine für Menschen lesbare Beschreibung des Protokollereignisses ist.  Üblicherweise wird dieser String als Markdown formatiert, wenn er präsentiert wird.

Die optionale Liste von `key=value`-Paaren unterstützt beliebige benutzerdefinierte Metadaten, die als Teil des Protokolleintrags an das Protokollierungssystem weitergegeben werden.  Wenn nur ein `value`-Ausdruck bereitgestellt wird, wird ein Schlüssel, der den Ausdruck darstellt, unter Verwendung von [`Symbol`](@ref) generiert. Zum Beispiel wird `x` zu `x=x`, und `foo(10)` wird zu `Symbol("foo(10)")=foo(10)`.  Um eine Liste von Schlüssel-Wert-Paaren zu splatten, verwenden Sie die normale Splattingsyntax, `@info "blah" kws...`.

Es gibt einige Schlüssel, die es ermöglichen, automatisch generierte Protokolldaten zu überschreiben:

  * `_module=mod` kann verwendet werden, um ein anderes Ursprungsmodul als den Quellort der Nachricht anzugeben.
  * `_group=symbol` kann verwendet werden, um die Nachrichten-Gruppe zu überschreiben (dies wird normalerweise aus dem Basisnamen der Quelldatei abgeleitet).
  * `_id=symbol` kann verwendet werden, um die automatisch generierte eindeutige Nachrichtenkennung zu überschreiben.  Dies ist nützlich, wenn Sie Nachrichten, die an verschiedenen Quellzeilen generiert wurden, sehr eng miteinander verknüpfen müssen.
  * `_file=string` und `_line=integer` können verwendet werden, um den scheinbaren Quellort einer Protokollnachricht zu überschreiben.

Es gibt auch einige Schlüssel-Wert-Paare, die eine konventionelle Bedeutung haben:

  * `maxlog=integer` sollte als Hinweis an das Backend verwendet werden, dass die Nachricht nicht mehr als `maxlog`-Mal angezeigt werden sollte.
  * `exception=ex` sollte verwendet werden, um eine Ausnahme mit einer Protokollnachricht zu transportieren, oft verwendet mit `@error`. Ein zugehöriger Backtrace `bt` kann unter Verwendung des Tupels `exception=(ex,bt)` angehängt werden.

# Beispiele

```

julia @debug "Ausführliche Debugging-Informationen.  Standardmäßig unsichtbar" @info  "Eine informative Nachricht" @warn  "Etwas war seltsam.  Sie sollten darauf achten" @error "Ein nicht fataler Fehler ist aufgetreten"

x = 10 @info "Einige Variablen, die an die Nachricht angehängt sind" x a=42.0

@debug begin     sA = sum(A)     "sum(A) = :sA ist eine teure Operation, die nur ausgewertet wird, wenn `shouldlog` true zurückgibt" end

for i=1:10000     @info "Mit dem Standard-Backend sehen Sie (i = :i) nur zehn Mal"  maxlog=10     @debug "Algorithmus1" i fortschritt=i/10000 end ```

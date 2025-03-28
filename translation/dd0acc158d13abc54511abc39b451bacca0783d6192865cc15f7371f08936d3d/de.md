```
pmap(f, [::AbstractWorkerPool], c...; distributed=true, batch_size=1, on_error=nothing, retry_delays=[], retry_check=nothing) -> Sammlung
```

Transformiere die Sammlung `c`, indem `f` auf jedes Element unter Verwendung verfügbarer Arbeiter und Aufgaben angewendet wird.

Bei mehreren Sammlungsargumenten wird `f` elementweise angewendet.

Beachte, dass `f` allen Arbeiterprozessen zur Verfügung stehen muss; siehe [Codeverfügbarkeit und Laden von Paketen](@ref code-availability) für Details.

Wenn kein Arbeiterpool angegeben ist, werden alle verfügbaren Arbeiter über einen [`CachingPool`](@ref) verwendet.

Standardmäßig verteilt `pmap` die Berechnung über alle angegebenen Arbeiter. Um nur den lokalen Prozess zu verwenden und über Aufgaben zu verteilen, gib `distributed=false` an. Dies entspricht der Verwendung von [`asyncmap`](@ref). Zum Beispiel ist `pmap(f, c; distributed=false)` äquivalent zu `asyncmap(f,c; ntasks=()->nworkers())`

`pmap` kann auch eine Mischung aus Prozessen und Aufgaben über das Argument `batch_size` verwenden. Bei Batchgrößen größer als 1 wird die Sammlung in mehreren Batches verarbeitet, die jeweils die Länge `batch_size` oder weniger haben. Ein Batch wird als einzelne Anfrage an einen freien Arbeiter gesendet, wo eine lokale [`asyncmap`](@ref) Elemente aus dem Batch mit mehreren gleichzeitigen Aufgaben verarbeitet.

Ein Fehler stoppt `pmap` daran, den Rest der Sammlung zu verarbeiten. Um dieses Verhalten zu überschreiben, kannst du eine Fehlerbehandlungsfunktion über das Argument `on_error` angeben, die ein einzelnes Argument, d.h. die Ausnahme, entgegennimmt. Die Funktion kann die Verarbeitung stoppen, indem sie den Fehler erneut auslöst, oder, um fortzufahren, einen beliebigen Wert zurückgeben, der dann inline mit den Ergebnissen an den Aufrufer zurückgegeben wird.

Betrachte die folgenden zwei Beispiele. Das erste gibt das Ausnahmeobjekt inline zurück, das zweite eine 0 anstelle einer Ausnahme:

```julia-repl
julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=identity)
4-element Array{Any,1}:
 1
  ErrorException("foo")
 3
  ErrorException("foo")

julia> pmap(x->iseven(x) ? error("foo") : x, 1:4; on_error=ex->0)
4-element Array{Int64,1}:
 1
 0
 3
 0
```

Fehler können auch behandelt werden, indem fehlgeschlagene Berechnungen erneut versucht werden. Die Schlüsselwortargumente `retry_delays` und `retry_check` werden als Schlüsselwortargumente `delays` und `check` an [`retry`](@ref) weitergegeben. Wenn das Batching angegeben ist und ein gesamter Batch fehlschlägt, werden alle Elemente im Batch erneut versucht.

Beachte, dass wenn sowohl `on_error` als auch `retry_delays` angegeben sind, der `on_error` Hook vor dem erneuten Versuch aufgerufen wird. Wenn `on_error` keine Ausnahme auslöst (oder erneut auslöst), wird das Element nicht erneut versucht.

Beispiel: Bei Fehlern, versuche `f` auf einem Element maximal 3 Mal ohne Verzögerung zwischen den Versuchen.

```julia
pmap(f, c; retry_delays = zeros(3))
```

Beispiel: Versuche `f` nur, wenn die Ausnahme nicht vom Typ [`InexactError`](@ref) ist, mit exponentiell zunehmenden Verzögerungen bis zu 3 Mal. Gib ein `NaN` anstelle aller `InexactError`-Vorkommen zurück.

```julia
pmap(f, c; on_error = e->(isa(e, InexactError) ? NaN : rethrow()), retry_delays = ExponentialBackOff(n = 3))
```

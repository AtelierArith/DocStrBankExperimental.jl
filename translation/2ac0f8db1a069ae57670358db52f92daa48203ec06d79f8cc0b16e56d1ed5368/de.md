```
SharedArray{T}(dims::NTuple; init=false, pids=Int[])
SharedArray{T,N}(...)
```

Konstruiere ein `SharedArray` eines Bits-Typs `T` und der Größe `dims` über die Prozesse, die durch `pids` angegeben sind - alle müssen sich auf demselben Host befinden. Wenn `N` durch den Aufruf von `SharedArray{T,N}(dims)` angegeben wird, muss `N` der Länge von `dims` entsprechen.

Wenn `pids` nicht angegeben wird, wird das gemeinsame Array über alle Prozesse auf dem aktuellen Host, einschließlich des Masters, abgebildet. Aber `localindices` und `indexpids` beziehen sich nur auf Arbeitsprozesse. Dies erleichtert den Code zur Arbeitsverteilung, um Arbeiter für die tatsächliche Berechnung zu verwenden, während der Masterprozess als Treiber fungiert.

Wenn eine `init`-Funktion des Typs `initfn(S::SharedArray)` angegeben ist, wird sie auf allen teilnehmenden Arbeitern aufgerufen.

Das gemeinsame Array ist gültig, solange eine Referenz auf das `SharedArray`-Objekt auf dem Knoten existiert, der die Abbildung erstellt hat.

```
SharedArray{T}(filename::AbstractString, dims::NTuple, [offset=0]; mode=nothing, init=false, pids=Int[])
SharedArray{T,N}(...)
```

Konstruiere ein `SharedArray`, das durch die Datei `filename` unterstützt wird, mit dem Elementtyp `T` (muss ein Bits-Typ sein) und der Größe `dims`, über die Prozesse, die durch `pids` angegeben sind - alle müssen sich auf demselben Host befinden. Diese Datei wird in den Host-Speicher mmapped, mit den folgenden Konsequenzen:

  * Die Array-Daten müssen im binären Format dargestellt werden (z. B. kann ein ASCII-Format wie CSV nicht unterstützt werden)
  * Alle Änderungen, die Sie an den Array-Werten vornehmen (z. B. `A[3] = 0`), ändern auch die Werte auf der Festplatte

Wenn `pids` nicht angegeben wird, wird das gemeinsame Array über alle Prozesse auf dem aktuellen Host, einschließlich des Masters, abgebildet. Aber `localindices` und `indexpids` beziehen sich nur auf Arbeitsprozesse. Dies erleichtert den Code zur Arbeitsverteilung, um Arbeiter für die tatsächliche Berechnung zu verwenden, während der Masterprozess als Treiber fungiert.

`mode` muss eines von `"r"`, `"r+"`, `"w+"` oder `"a+"` sein und standardmäßig auf `"r+"` gesetzt werden, wenn die durch `filename` angegebene Datei bereits existiert, oder auf `"w+"`, wenn nicht. Wenn eine `init`-Funktion des Typs `initfn(S::SharedArray)` angegeben ist, wird sie auf allen teilnehmenden Arbeitern aufgerufen. Sie können keine `init`-Funktion angeben, wenn die Datei nicht beschreibbar ist.

`offset` ermöglicht es Ihnen, die angegebene Anzahl von Bytes am Anfang der Datei zu überspringen.

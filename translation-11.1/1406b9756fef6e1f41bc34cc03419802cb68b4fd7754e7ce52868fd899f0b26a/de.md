```
Ref{T}
```

Ein Objekt, das sicher auf Daten des Typs `T` verweist. Dieser Typ garantiert, dass er auf gültigen, in Julia zugewiesenen Speicher des richtigen Typs zeigt. Die zugrunde liegenden Daten sind vor der Freigabe durch den Garbage Collector geschützt, solange der `Ref` selbst referenziert wird.

In Julia werden `Ref`-Objekte mit `[]` dereferenziert (geladen oder gespeichert).

Die Erstellung eines `Ref` auf einen Wert `x` des Typs `T` wird normalerweise als `Ref(x)` geschrieben. Darüber hinaus kann für die Erstellung von Innenzeigern auf Container (wie Array oder Ptr) `Ref(a, i)` geschrieben werden, um eine Referenz auf das `i`-te Element von `a` zu erstellen.

`Ref{T}()` erstellt eine Referenz auf einen Wert des Typs `T` ohne Initialisierung. Für einen Bittyp `T` wird der Wert das sein, was derzeit im zugewiesenen Speicher vorhanden ist. Für einen Nicht-Bittyp `T` wird die Referenz undefiniert sein, und der Versuch, sie zu dereferenzieren, führt zu einem Fehler: "UndefRefError: Zugriff auf undefinierte Referenz".

Um zu überprüfen, ob ein `Ref` eine undefinierte Referenz ist, verwenden Sie [`isassigned(ref::RefValue)`](@ref). Zum Beispiel ist `isassigned(Ref{T}())` `false`, wenn `T` kein Bittyp ist. Wenn `T` ein Bittyp ist, wird `isassigned(Ref{T}())` immer `true` sein.

Wenn als `ccall`-Argument übergeben (entweder als `Ptr` oder `Ref`-Typ), wird ein `Ref`-Objekt in einen nativen Zeiger auf die Daten, auf die es verweist, umgewandelt. Für die meisten `T` oder wenn es in einen `Ptr{Cvoid}` umgewandelt wird, ist dies ein Zeiger auf die Objekt-Daten. Wenn `T` ein `isbits`-Typ ist, kann dieser Wert sicher verändert werden, andernfalls ist die Mutation strikt undefiniertes Verhalten.

In einem Sonderfall führt das Setzen von `T = Any` stattdessen zur Erstellung eines Zeigers auf die Referenz selbst, wenn es in einen `Ptr{Any}` umgewandelt wird (ein `jl_value_t const* const*`, wenn T unveränderlich ist, andernfalls ein `jl_value_t *const *`). Wenn es in einen `Ptr{Cvoid}` umgewandelt wird, gibt es weiterhin einen Zeiger auf den Datenbereich wie für jeden anderen `T`.

Eine `C_NULL`-Instanz von `Ptr` kann als `ccall`-`Ref`-Argument übergeben werden, um sie zu initialisieren.

# Verwendung in Broadcasting

`Ref` wird manchmal im Broadcasting verwendet, um die referenzierten Werte als Skalar zu behandeln.

# Beispiele

```jldoctest
julia> r = Ref(5) # Erstellen Sie einen Ref mit einem Anfangswert
Base.RefValue{Int64}(5)

julia> r[] # Einen Wert aus einem Ref abrufen
5

julia> r[] = 7 # Einen neuen Wert in einen Ref speichern
7

julia> r # Der Ref enthält jetzt 7
Base.RefValue{Int64}(7)

julia> isa.(Ref([1,2,3]), [Array, Dict, Int]) # Referenzwerte während des Broadcastings als Skalar behandeln
3-element BitVector:
 1
 0
 0

julia> Ref{Function}()  # Undefinierte Referenz auf einen Nicht-Bittyp, Funktion
Base.RefValue{Function}(#undef)

julia> try
           Ref{Function}()[] # Dereferenzieren einer undefinierten Referenz führt zu einem Fehler
       catch e
           println(e)
       end
UndefRefError()

julia> Ref{Int64}()[]; # Eine Referenz auf einen Bittyp verweist auf einen unbestimmten Wert, wenn nicht angegeben

julia> isassigned(Ref{Int64}()) # Eine Referenz auf einen Bittyp ist immer zugewiesen
true
```

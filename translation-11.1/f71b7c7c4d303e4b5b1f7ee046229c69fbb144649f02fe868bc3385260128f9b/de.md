```
IOContext(io::IO, KV::Pair...)
```

Erstellen Sie ein `IOContext`, das einen gegebenen Stream umschließt und die angegebenen `key=>value`-Paare zu den Eigenschaften dieses Streams hinzufügt (beachten Sie, dass `io` selbst ein `IOContext` sein kann).

  * Verwenden Sie `(key => value) in io`, um zu sehen, ob diese spezielle Kombination in der Eigenschaftenmenge enthalten ist.
  * Verwenden Sie `get(io, key, default)`, um den aktuellsten Wert für einen bestimmten Schlüssel abzurufen.

Die folgenden Eigenschaften sind allgemein in Gebrauch:

  * `:compact`: Boolean, der angibt, dass Werte kompakter gedruckt werden sollten, z. B. dass Zahlen mit weniger Ziffern gedruckt werden sollten. Dies wird beim Drucken von Array-Elementen gesetzt. Die `:compact`-Ausgabe sollte keine Zeilenumbrüche enthalten.
  * `:limit`: Boolean, der angibt, dass Container abgeschnitten werden sollten, z. B. dass `…` anstelle der meisten Elemente angezeigt wird.
  * `:displaysize`: Ein `Tuple{Int,Int}`, das die Größe in Zeilen und Spalten angibt, die für die Textausgabe verwendet werden soll. Dies kann verwendet werden, um die Anzeigegröße für aufgerufene Funktionen zu überschreiben, aber um die Größe des Bildschirms zu erhalten, verwenden Sie die Funktion `displaysize`.
  * `:typeinfo`: ein `Type`, der die Informationen charakterisiert, die bereits über den Typ des Objekts, das angezeigt werden soll, gedruckt wurden. Dies ist hauptsächlich nützlich, wenn eine Sammlung von Objekten desselben Typs angezeigt wird, sodass redundante Typinformationen vermieden werden können (z. B. kann `[Float16(0)]` als "Float16[0.0]" anstelle von "Float16[Float16(0.0)]" angezeigt werden: während die Elemente des Arrays angezeigt werden, wird die `:typeinfo`-Eigenschaft auf `Float16` gesetzt).
  * `:color`: Boolean, der angibt, ob ANSI-Farben-/Escape-Codes unterstützt/erwartet werden. Standardmäßig wird dies bestimmt, indem geprüft wird, ob `io` ein kompatibles Terminal ist und durch ein beliebiges `--color`-Kommandozeilenflag, als `julia` gestartet wurde.

# Beispiele

```jldoctest
julia> io = IOBuffer();

julia> printstyled(IOContext(io, :color => true), "string", color=:red)

julia> String(take!(io))
"\e[31mstring\e[39m"

julia> printstyled(io, "string", color=:red)

julia> String(take!(io))
"string"
```

```jldoctest
julia> print(IOContext(stdout, :compact => false), 1.12341234)
1.12341234
julia> print(IOContext(stdout, :compact => true), 1.12341234)
1.12341
```

```jldoctest
julia> function f(io::IO)
           if get(io, :short, false)
               print(io, "short")
           else
               print(io, "loooooong")
           end
       end
f (generische Funktion mit 1 Methode)

julia> f(stdout)
loooooong
julia> f(IOContext(stdout, :short => true))
short
```

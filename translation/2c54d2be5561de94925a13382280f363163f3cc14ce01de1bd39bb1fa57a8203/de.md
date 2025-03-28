```
show([io::IO = stdout], x)
```

Schreibt eine Textdarstellung eines Wertes `x` in den Ausgabestrom `io`. Neue Typen `T` sollten `show(io::IO, x::T)` überladen. Die von `show` verwendete Darstellung umfasst in der Regel Julia-spezifische Formatierung und Typinformationen und sollte, wenn möglich, als Julia-Code analysierbar sein.

[`repr`](@ref) gibt die Ausgabe von `show` als Zeichenfolge zurück.

Für eine ausführlichere, menschenlesbare Textausgabe für Objekte des Typs `T` definieren Sie zusätzlich `show(io::IO, ::MIME"text/plain", ::T)`. Es wird empfohlen, den `:compact` [`IOContext`](@ref) Schlüssel (häufig überprüft als `get(io, :compact, false)::Bool`) von `io` in solchen Methoden zu überprüfen, da einige Container ihre Elemente anzeigen, indem sie diese Methode mit `:compact => true` aufrufen.

Siehe auch [`print`](@ref), das un-dekorierte Darstellungen schreibt.

# Beispiele

```jldoctest
julia> show("Hello World!")
"Hello World!"
julia> print("Hello World!")
Hello World!
```

```
base64encode(writefunc, args...; context=nothing)
base64encode(args...; context=nothing)
```

Gegeben einer [`write`](@ref)-ähnlichen Funktion `writefunc`, die einen I/O-Stream als ihr erstes Argument nimmt, ruft `base64encode(writefunc, args...)` `writefunc` auf, um `args...` in einen base64-kodierten String zu schreiben, und gibt den String zurück. `base64encode(args...)` ist äquivalent zu `base64encode(write, args...)`: es konvertiert seine Argumente in Bytes unter Verwendung der standardmäßigen [`write`](@ref)-Funktionen und gibt den base64-kodierten String zurück.

Das optionale Schlüsselwort-Argument `context` kann auf ein `:key=>value`-Paar oder ein `IO`- oder [`IOContext`](@ref)-Objekt gesetzt werden, dessen Attribute für den I/O-Stream verwendet werden, der an `writefunc` oder `write` übergeben wird.

Siehe auch [`base64decode`](@ref).

```
stringmime(mime, x; context=nothing)
```

Gibt einen `AbstractString` zurück, der die Darstellung von `x` im angeforderten `mime`-Typ enthält. Dies ist ähnlich wie [`repr(mime, x)`](@ref), mit dem Unterschied, dass Binärdaten als ASCII-Zeichenfolge in Base64 kodiert werden.

Das optionale Schlüsselwort-Argument `context` kann auf ein `:key=>value`-Paar oder ein `IO`- oder [`IOContext`](@ref)-Objekt gesetzt werden, dessen Attribute für den I/O-Stream verwendet werden, der an [`show`](@ref) übergeben wird.

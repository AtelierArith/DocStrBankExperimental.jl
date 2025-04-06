```
repr(mime, x; context=nothing)
```

Gibt eine `AbstractString` oder `Vector{UInt8}` zurück, die die Darstellung von `x` im angeforderten `mime`-Typ enthält, wie von [`show(io, mime, x)`](@ref) geschrieben (wirft einen [`MethodError`](@ref), wenn keine geeignete `show` verfügbar ist). Eine `AbstractString` wird für MIME-Typen mit textuellen Darstellungen (wie `"text/html"` oder `"application/postscript"`) zurückgegeben, während binäre Daten als `Vector{UInt8}` zurückgegeben werden. (Die Funktion `istextmime(mime)` gibt zurück, ob Julia einen bestimmten `mime`-Typ als Text behandelt.)

Das optionale Schlüsselwort-Argument `context` kann auf ein `:key=>value`-Paar oder ein `IO`- oder [`IOContext`](@ref)-Objekt gesetzt werden, dessen Attribute für den I/O-Stream verwendet werden, der an `show` übergeben wird.

In einem speziellen Fall, wenn `x` eine `AbstractString` (für textuelle MIME-Typen) oder ein `Vector{UInt8}` (für binäre MIME-Typen) ist, geht die `repr`-Funktion davon aus, dass `x` bereits im angeforderten `mime`-Format vorliegt und gibt einfach `x` zurück. Dieser Sonderfall gilt nicht für den MIME-Typ `"text/plain"`. Dies ist nützlich, damit Rohdaten an `display(m::MIME, x)` übergeben werden können.

Insbesondere ist `repr("text/plain", x)` typischerweise eine "schön formatierte" Version von `x`, die für den menschlichen Konsum gedacht ist. Siehe auch [`repr(x)`](@ref), um stattdessen eine Zeichenfolge zurückzugeben, die [`show(x)`](@ref) entspricht und näher daran sein könnte, wie der Wert von `x` in Julia eingegeben werden würde.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4];

julia> repr("text/plain", A)
"2×2 Matrix{Int64}:\n 1  2\n 3  4"
```

```
Expr(head::Symbol, args...)
```

Ein Typ, der zusammengesetzte Ausdrücke im geparsten Julia-Code (ASTs) darstellt. Jeder Ausdruck besteht aus einem `head` `Symbol`, das angibt, um welche Art von Ausdruck es sich handelt (z. B. einen Aufruf, eine Schleife, eine bedingte Anweisung usw.), und Unterausdrücken (z. B. die Argumente eines Aufrufs). Die Unterausdrücke werden in einem `Vector{Any}`-Feld namens `args` gespeichert.

Siehe das Handbuchkapitel über [Metaprogrammierung](@ref) und die Entwicklermokumentation [Julia ASTs](@ref).

# Beispiele

```jldoctest
julia> Expr(:call, :+, 1, 2)
:(1 + 2)

julia> dump(:(a ? b : c))
Expr
  head: Symbol if
  args: Array{Any}((3,))
    1: Symbol a
    2: Symbol b
    3: Symbol c
```

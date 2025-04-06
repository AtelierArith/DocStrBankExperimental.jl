```
mapreduce(f, op, itrs...; [init])
```

Wenden Sie die Funktion `f` auf jedes Element(e) in `itrs` an und reduzieren Sie dann das Ergebnis mit der binären Funktion `op`. Wenn angegeben, muss `init` ein neutrales Element für `op` sein, das für leere Sammlungen zurückgegeben wird. Es ist nicht festgelegt, ob `init` für nicht-leere Sammlungen verwendet wird. Im Allgemeinen ist es notwendig, `init` bereitzustellen, um mit leeren Sammlungen zu arbeiten.

[`mapreduce`](@ref) ist funktional äquivalent zu einem Aufruf von `reduce(op, map(f, itr); init=init)`, wird jedoch im Allgemeinen schneller ausgeführt, da keine Zwischenkollektion erstellt werden muss. Siehe Dokumentation für [`reduce`](@ref) und [`map`](@ref).

!!! compat "Julia 1.2"
    `mapreduce` mit mehreren Iteratoren erfordert Julia 1.2 oder später.


# Beispiele

```jldoctest
julia> mapreduce(x->x^2, +, [1:3;]) # == 1 + 4 + 9
14
```

Die Assoziativität der Reduktion ist implementationsabhängig. Darüber hinaus können einige Implementierungen den Rückgabewert von `f` für Elemente wiederverwenden, die mehrfach in `itr` erscheinen. Verwenden Sie stattdessen [`mapfoldl`](@ref) oder [`mapfoldr`](@ref) für garantierte linke oder rechte Assoziativität und die Ausführung von `f` für jeden Wert.

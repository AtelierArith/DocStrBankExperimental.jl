```
repr(x; context=nothing)
```

Erstellen Sie einen String aus jedem Wert mit der [`show`](@ref) Funktion. Sie sollten keine Methoden zu `repr` hinzufügen; definieren Sie stattdessen eine `show` Methode.

Das optionale Schlüsselwort-Argument `context` kann auf ein `:key=>value` Paar, ein Tupel von `:key=>value` Paaren oder ein `IO` oder [`IOContext`](@ref) Objekt gesetzt werden, dessen Attribute für den I/O-Stream verwendet werden, der an `show` übergeben wird.

Beachten Sie, dass `repr(x)` normalerweise ähnlich ist, wie der Wert von `x` in Julia eingegeben werden würde. Siehe auch [`repr(MIME("text/plain"), x)`](@ref), um stattdessen eine "schön formatierte" Version von `x` zurückzugeben, die mehr für den menschlichen Konsum gedacht ist, was dem REPL-Display von `x` entspricht.

!!! compat "Julia 1.7"
    Das Übergeben eines Tupels an das Schlüsselwort `context` erfordert Julia 1.7 oder höher.


# Beispiele

```jldoctest
julia> repr(1)
"1"

julia> repr(zeros(3))
"[0.0, 0.0, 0.0]"

julia> repr(big(1/3))
"0.333333333333333314829616256247390992939472198486328125"

julia> repr(big(1/3), context=:compact => true)
"0.333333"
```

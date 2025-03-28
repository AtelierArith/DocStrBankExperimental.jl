```
eachrsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachrsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Gibt einen Iterator über `SubString`s von `str` zurück, die beim Splitten an dem Trennzeichen `dlm` erzeugt werden und in umgekehrter Reihenfolge (von rechts nach links) ausgegeben werden. `dlm` kann eines der Formate sein, die als erstes Argument von [`findprev`](@ref) erlaubt sind (d.h. ein String, ein einzelnes Zeichen oder eine Funktion) oder eine Sammlung von Zeichen.

Wenn `dlm` weggelassen wird, wird standardmäßig [`isspace`](@ref) verwendet, und `keepempty` standardmäßig auf `false` gesetzt.

Die optionalen Schlüsselwortargumente sind:

  * Wenn `limit > 0`, wird der Iterator höchstens `limit - 1` Mal splitten, bevor der Rest des Strings ungeteilt zurückgegeben wird. `limit < 1` bedeutet keine Begrenzung der Splits (Standard).
  * `keepempty`: ob leere Felder beim Iterieren zurückgegeben werden sollen. Standard ist `false` ohne ein `dlm`-Argument, `true` mit einem `dlm`-Argument.

Beachten Sie, dass diese Funktion im Gegensatz zu [`split`](@ref), [`rsplit`](@ref) und [`eachsplit`](@ref) die Teilstrings von rechts nach links iteriert, wie sie im Eingabetext vorkommen.

Siehe auch [`eachsplit`](@ref), [`rsplit`](@ref).

!!! compat "Julia 1.11"
    Diese Funktion erfordert Julia 1.11 oder höher.


# Beispiele

```jldoctest
julia> a = "Ma.r.ch";

julia> collect(eachrsplit(a, ".")) == ["ch", "r", "Ma"]
true

julia> collect(eachrsplit(a, "."; limit=2)) == ["ch", "Ma.r"]
true
```

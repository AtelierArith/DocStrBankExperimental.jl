```
string(xs...)
```

Erstellen Sie eine Zeichenkette aus beliebigen Werten mit der [`print`](@ref) Funktion.

`string` sollte normalerweise nicht direkt definiert werden. Stattdessen definieren Sie eine Methode `print(io::IO, x::MyType)`. Wenn `string(x)` für einen bestimmten Typ sehr effizient sein muss, kann es sinnvoll sein, eine Methode zu `string` hinzuzufügen und `print(io::IO, x::MyType) = print(io, string(x))` zu definieren, um sicherzustellen, dass die Funktionen konsistent sind.

Siehe auch: [`String`](@ref), [`repr`](@ref), [`sprint`](@ref), [`show`](@ref @show).

# Beispiele

```jldoctest
julia> string("a", 1, true)
"a1true"
```

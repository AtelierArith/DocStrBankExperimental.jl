```
any(itr) -> Bool
```

Überprüfen, ob Elemente einer booleschen Sammlung `true` sind, und `true` zurückgeben, sobald der erste `true`-Wert in `itr` gefunden wird (Kurzschluss). Um bei `false` einen Kurzschluss zu machen, verwenden Sie [`all`](@ref).

Wenn die Eingabe [`missing`](@ref) Werte enthält, geben Sie `missing` zurück, wenn alle nicht fehlenden Werte `false` sind (oder äquivalent, wenn die Eingabe keinen `true`-Wert enthält), gemäß der [dreiwertigen Logik](https://en.wikipedia.org/wiki/Three-valued_logic).

Siehe auch: [`all`](@ref), [`count`](@ref), [`sum`](@ref), [`|`](@ref), , [`||`](@ref).

# Beispiele

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> any(a)
true

julia> any((println(i); v) for (i, v) in enumerate(a))
1
true

julia> any([missing, true])
true

julia> any([false, missing])
missing
```

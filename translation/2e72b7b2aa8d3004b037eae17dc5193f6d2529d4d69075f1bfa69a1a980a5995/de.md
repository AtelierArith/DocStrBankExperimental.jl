```
all(itr) -> Bool
```

Überprüfen, ob alle Elemente einer booleschen Sammlung `true` sind, und `false` zurückgeben, sobald der erste `false`-Wert in `itr` gefunden wird (Short-Circuiting). Um bei `true` einen Short-Circuit zu machen, verwenden Sie [`any`](@ref).

Wenn die Eingabe [`missing`](@ref) Werte enthält, geben Sie `missing` zurück, wenn alle nicht fehlenden Werte `true` sind (oder äquivalent, wenn die Eingabe keinen `false`-Wert enthält), gemäß der [dreiwertigen Logik](https://en.wikipedia.org/wiki/Three-valued_logic).

Siehe auch: [`all!`](@ref), [`any`](@ref), [`count`](@ref), [`&`](@ref), , [`&&`](@ref), [`allunique`](@ref).

# Beispiele

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> all(a)
false

julia> all((println(i); v) for (i, v) in enumerate(a))
1
2
false

julia> all([missing, false])
false

julia> all([true, missing])
missing
```

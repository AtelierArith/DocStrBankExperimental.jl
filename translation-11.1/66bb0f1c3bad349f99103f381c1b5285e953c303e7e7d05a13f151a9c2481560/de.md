```
convert(T, x)
```

Konvertiere `x` in einen Wert des Typs `T`.

Wenn `T` ein [`Integer`](@ref) Typ ist, wird ein [`InexactError`](@ref) ausgelöst, wenn `x` nicht durch `T` darstellbar ist, zum Beispiel wenn `x` keinen ganzzahligen Wert hat oder außerhalb des von `T` unterstützten Bereichs liegt.

# Beispiele

```jldoctest
julia> convert(Int, 3.0)
3

julia> convert(Int, 3.5)
ERROR: InexactError: Int64(3.5)
Stacktrace:
[...]
```

Wenn `T` ein [`AbstractFloat`](@ref) Typ ist, wird der nächstgelegene Wert zu `x`, der durch `T` darstellbar ist, zurückgegeben. Inf wird für die Bestimmung des Nächsten als um eine ulp größer als `floatmax(T)` behandelt.

```jldoctest
julia> x = 1/3
0.3333333333333333

julia> convert(Float32, x)
0.33333334f0

julia> convert(BigFloat, x)
0.333333333333333314829616256247390992939472198486328125
```

Wenn `T` ein Sammlungstyp ist und `x` eine Sammlung, kann das Ergebnis von `convert(T, x)` ganz oder teilweise mit `x` übereinstimmen.

```jldoctest
julia> x = Int[1, 2, 3];

julia> y = convert(Vector{Int}, x);

julia> y === x
true
```

Siehe auch: [`round`](@ref), [`trunc`](@ref), [`oftype`](@ref), [`reinterpret`](@ref).

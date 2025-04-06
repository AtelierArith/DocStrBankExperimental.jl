```
reduce(f, A::AbstractArray; dims=:, [init])
```

Reduziere die 2-Argumente-Funktion `f` entlang der Dimensionen von `A`. `dims` ist ein Vektor, der die zu reduzierenden Dimensionen angibt, und das Schlüsselwort-Argument `init` ist der Anfangswert, der in den Reduktionen verwendet werden soll. Für `+`, `*`, `max` und `min` ist das `init`-Argument optional.

Die Assoziativität der Reduktion ist implementationsabhängig; wenn Sie eine bestimmte Assoziativität benötigen, z. B. von links nach rechts, sollten Sie Ihre eigene Schleife schreiben oder in Betracht ziehen, [`foldl`](@ref) oder [`foldr`](@ref) zu verwenden. Siehe Dokumentation für [`reduce`](@ref).

# Beispiele

```jldoctest
julia> a = reshape(Vector(1:16), (4,4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reduce(max, a, dims=2)
4×1 Matrix{Int64}:
 13
 14
 15
 16

julia> reduce(max, a, dims=1)
1×4 Matrix{Int64}:
 4  8  12  16
```

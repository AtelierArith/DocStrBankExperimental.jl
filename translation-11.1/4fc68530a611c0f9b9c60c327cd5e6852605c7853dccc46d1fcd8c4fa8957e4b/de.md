```
dropdims(A; dims)
```

Gibt ein Array mit denselben Daten wie `A` zurück, jedoch mit den durch `dims` angegebenen Dimensionen entfernt. `size(A,d)` muss für jedes `d` in `dims` gleich 1 sein, und wiederholte Dimensionen oder Zahlen außerhalb von `1:ndims(A)` sind verboten.

Das Ergebnis teilt sich die gleichen zugrunde liegenden Daten wie `A`, sodass das Ergebnis veränderlich ist, wenn und nur wenn `A` veränderlich ist, und das Setzen von Elementen eines das Werte des anderen verändert.

Siehe auch: [`reshape`](@ref), [`vec`](@ref).

# Beispiele

```jldoctest
julia> a = reshape(Vector(1:4),(2,2,1,1))
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

julia> b = dropdims(a; dims=3)
2×2×1 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

julia> b[1,1,1] = 5; a
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 5  3
 2  4
```

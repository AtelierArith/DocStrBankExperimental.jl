```
prevind(A, i)
```

Gibt den Index vor `i` in `A` zurück. Der zurückgegebene Index entspricht oft `i - 1` für ein ganzzahliges `i`. Diese Funktion kann für generischen Code nützlich sein.

!!! warning
    Der zurückgegebene Index könnte außerhalb der Grenzen liegen. Ziehen Sie in Betracht, [`checkbounds`](@ref) zu verwenden.


Siehe auch: [`nextind`](@ref).

# Beispiele

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prevind(x, 4) # gültiges Ergebnis
3

julia> prevind(x, 1) # ungültiges Ergebnis
0

julia> prevind(x, CartesianIndex(2, 2)) # gültiges Ergebnis
CartesianIndex(1, 2)

julia> prevind(x, CartesianIndex(1, 1)) # ungültiges Ergebnis
CartesianIndex(2, 0)
```

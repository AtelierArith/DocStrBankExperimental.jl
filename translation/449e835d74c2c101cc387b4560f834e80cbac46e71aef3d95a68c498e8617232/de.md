```
nextind(A, i)
```

Gibt den Index nach `i` in `A` zurück. Der zurückgegebene Index entspricht oft `i + 1` für ein ganzzahliges `i`. Diese Funktion kann für generischen Code nützlich sein.

!!! warning
    Der zurückgegebene Index könnte außerhalb der Grenzen liegen. Ziehen Sie in Betracht, [`checkbounds`](@ref) zu verwenden.


Siehe auch: [`prevind`](@ref).

# Beispiele

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nextind(x, 1) # gültiges Ergebnis
2

julia> nextind(x, 4) # ungültiges Ergebnis
5

julia> nextind(x, CartesianIndex(1, 1)) # gültiges Ergebnis
CartesianIndex(2, 1)

julia> nextind(x, CartesianIndex(2, 2)) # ungültiges Ergebnis
CartesianIndex(1, 3)
```

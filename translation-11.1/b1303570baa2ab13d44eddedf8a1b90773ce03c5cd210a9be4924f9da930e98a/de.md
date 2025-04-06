```
unique!(A::AbstractVector)
```

Entfernen Sie doppelte Elemente, wie sie durch [`isequal`](@ref) und [`hash`](@ref) bestimmt werden, und geben Sie dann das modifizierte `A` zurück. `unique!` gibt die Elemente von `A` in der Reihenfolge zurück, in der sie auftreten. Wenn Ihnen die Reihenfolge der zurückgegebenen Daten egal ist, dann ist der Aufruf von `(sort!(A); unique!(A))` viel effizienter, solange die Elemente von `A` sortiert werden können.

# Beispiele

```jldoctest
julia> unique!([1, 1, 1])
1-element Vector{Int64}:
 1

julia> A = [7, 3, 2, 3, 7, 5];

julia> unique!(A)
4-element Vector{Int64}:
 7
 3
 2
 5

julia> B = [7, 6, 42, 6, 7, 42];

julia> sort!(B);  # unique! kann sortierte Daten viel effizienter verarbeiten.

julia> unique!(B)
3-element Vector{Int64}:
  6
  7
 42
```

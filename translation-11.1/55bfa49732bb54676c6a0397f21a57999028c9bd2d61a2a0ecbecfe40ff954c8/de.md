```
splice!(a::Vector, indices, [replacement]) -> items
```

Entfernt Elemente an den angegebenen Indizes und gibt eine Sammlung der entfernten Elemente zurück. Nachfolgende Elemente werden nach links verschoben, um die entstehenden Lücken zu füllen. Wenn angegeben, werden Ersatzwerte aus einer geordneten Sammlung anstelle der entfernten Elemente eingefügt; in diesem Fall muss `indices` ein `AbstractUnitRange` sein.

Um `replacement` vor einem Index `n` einzufügen, ohne Elemente zu entfernen, verwenden Sie `splice!(collection, n:n-1, replacement)`.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


!!! compat "Julia 1.5"
    Vor Julia 1.5 musste `indices` immer ein `UnitRange` sein.


!!! compat "Julia 1.8"
    Vor Julia 1.8 musste `indices` ein `UnitRange` sein, wenn Ersatzwerte eingefügt wurden.


# Beispiele

```jldoctest
julia> A = [-1, -2, -3, 5, 4, 3, -1]; splice!(A, 4:3, 2)
Int64[]

julia> A
8-element Vector{Int64}:
 -1
 -2
 -3
  2
  5
  4
  3
 -1
```

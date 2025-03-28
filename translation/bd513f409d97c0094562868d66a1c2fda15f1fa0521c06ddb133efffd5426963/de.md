```
splice!(a::Vector, index::Integer, [replacement]) -> item
```

Entfernt das Element am angegebenen Index und gibt das entfernte Element zurück. Nachfolgende Elemente werden nach links verschoben, um die entstandene Lücke zu füllen. Wenn angegeben, werden Ersatzwerte aus einer geordneten Sammlung anstelle des entfernten Elements eingefügt.

Siehe auch: [`replace`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`pop!`](@ref), [`popat!`](@ref).

# Beispiele

```jldoctest
julia> A = [6, 5, 4, 3, 2, 1]; splice!(A, 5)
2

julia> A
5-element Vector{Int64}:
 6
 5
 4
 3
 1

julia> splice!(A, 5, -1)
1

julia> A
5-element Vector{Int64}:
  6
  5
  4
  3
 -1

julia> splice!(A, 1, [-1, -2, -3])
6

julia> A
7-element Vector{Int64}:
 -1
 -2
 -3
  5
  4
  3
 -1
```

Um `replacement` vor einem Index `n` einzufügen, ohne Elemente zu entfernen, verwenden Sie `splice!(collection, n:n-1, replacement)`.

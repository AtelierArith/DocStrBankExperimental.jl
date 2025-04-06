```
Iterators.flatmap(f, iterators...)
```

`flatten(map(f, iterators...))` ile eşdeğerdir.

Ayrıca bkz. [`Iterators.flatten`](@ref), [`Iterators.map`](@ref).

!!! compat "Julia 1.9"
    Bu fonksiyon Julia 1.9'da eklendi.


# Örnekler

```jldoctest
julia> Iterators.flatmap(n -> -n:2:n, 1:3) |> collect
9-element Vector{Int64}:
 -1
  1
 -2
  0
  2
 -3
 -1
  1
  3

julia> stack(n -> -n:2:n, 1:3)
HATA: DimensionMismatch: stack uniform dilimler bekliyor, axes(x) == (1:3,) iken ilki (1:2,) aldı.
[...]

julia> Iterators.flatmap(n -> (-n, 10n), 1:2) |> collect
4-element Vector{Int64}:
 -1
 10
 -2
 20

julia> ans == vec(stack(n -> (-n, 10n), 1:2))
true
```

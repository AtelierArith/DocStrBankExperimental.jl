```
Iterators.flatmap(f, iterators...)
```

Entspricht `flatten(map(f, iterators...))`.

Siehe auch [`Iterators.flatten`](@ref), [`Iterators.map`](@ref).

!!! compat "Julia 1.9"
    Diese Funktion wurde in Julia 1.9 hinzugefügt.


# Beispiele

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
ERROR: DimensionMismatch: stack erwartet einheitliche Schnitte, erhielt axes(x) == (1:3,) während der erste (1:2,) hatte
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

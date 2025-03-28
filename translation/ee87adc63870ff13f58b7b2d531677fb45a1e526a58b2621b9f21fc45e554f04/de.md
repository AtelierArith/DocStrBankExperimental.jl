```
replace!(A, old_new::Pair...; [count::Integer])
```

Für jedes Paar `old=>new` in `old_new` ersetze alle Vorkommen von `old` in der Sammlung `A` durch `new`. Die Gleichheit wird mit [`isequal`](@ref) bestimmt. Wenn `count` angegeben ist, dann ersetze höchstens `count` Vorkommen insgesamt. Siehe auch [`replace`](@ref replace(A, old_new::Pair...)).

# Beispiele

```jldoctest
julia> replace!([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace!(Set([1, 2, 3]), 1=>0)
Set{Int64} mit 3 Elementen:
  0
  2
  3
```

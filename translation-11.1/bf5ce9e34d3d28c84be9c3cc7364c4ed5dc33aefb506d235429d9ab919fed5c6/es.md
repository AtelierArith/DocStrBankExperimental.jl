```
replace!(new::Union{Function, Type}, A; [count::Integer])
```

Reemplaza cada elemento `x` en la colección `A` por `new(x)`. Si se especifica `count`, entonces reemplaza como máximo `count` valores en total (los reemplazos se definen como `new(x) !== x`).

# Ejemplos

```jldoctest
julia> replace!(x -> isodd(x) ? 2x : x, [1, 2, 3, 4])
4-element Vector{Int64}:
 2
 2
 6
 4

julia> replace!(Dict(1=>2, 3=>4)) do kv
           first(kv) < 3 ? first(kv)=>3 : kv
       end
Dict{Int64, Int64} with 2 entries:
  3 => 4
  1 => 3

julia> replace!(x->2x, Set([3, 6]))
Set{Int64} with 2 elements:
  6
  12
```

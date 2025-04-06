```
replace!(new::Union{Function, Type}, A; [count::Integer])
```

Ersetze jedes Element `x` in der Sammlung `A` durch `new(x)`. Wenn `count` angegeben ist, dann ersetze höchstens `count` Werte insgesamt (Ersatz wird definiert als `new(x) !== x`).

# Beispiele

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
Dict{Int64, Int64} mit 2 Einträgen:
  3 => 4
  1 => 3

julia> replace!(x->2x, Set([3, 6]))
Set{Int64} mit 2 Elementen:
  6
  12
```

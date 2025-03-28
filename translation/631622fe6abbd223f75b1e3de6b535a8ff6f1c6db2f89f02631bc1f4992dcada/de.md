```
replace(new::Union{Function, Type}, A; [count::Integer])
```

Gibt eine Kopie von `A` zurück, in der jeder Wert `x` in `A` durch `new(x)` ersetzt wird. Wenn `count` angegeben ist, werden höchstens `count` Werte insgesamt ersetzt (Ersetzungen werden definiert als `new(x) !== x`).

!!! compat "Julia 1.7"
    Version 1.7 ist erforderlich, um Elemente eines `Tuple` zu ersetzen.


# Beispiele

```jldoctest
julia> replace(x -> isodd(x) ? 2x : x, [1, 2, 3, 4])
4-element Vector{Int64}:
 2
 2
 6
 4

julia> replace(Dict(1=>2, 3=>4)) do kv
           first(kv) < 3 ? first(kv)=>3 : kv
       end
Dict{Int64, Int64} mit 2 Einträgen:
  3 => 4
  1 => 3
```
